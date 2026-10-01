
          curl -X POST \
            "https://api.render.com/v1/services/${{ secrets.RENDER_ADS_SERVICE_ID }}/deploys" \
            -H "Authorization: Bearer ${{ secrets.RENDER_API_KEY }}" \
            -H "Content-Type: application/json" \
            -d '{}'

      - name: ✅ Confirm Deploy
        run: echo "✅ Ads Website deployment triggered!"

  
            -H "Content-Type: application/json" \
            -d '{}'

      - name: ✅ Confirm Deploy
        run: echo "✅ Skill Website deployment triggered!"

  # ============================
  # 📊 تقرير النشر
  # ============================
  notify:
    name: 📊 Deploy Report
    runs-on: ubuntu-latest
    needs: [deploy-main, deploy-ads, deploy-imperial, deploy-skill]
    if: always()
    steps:
      - name: 📊 Report
        run: |
          echo "================================"
          echo "🎨 ALAAGHA Deploy Report"
          echo "================================"
          echo "🔐 Main:     ${{ needs.deploy-main.result }}"
          echo "📢 Ads:      ${{ needs.deploy-ads.result }}"
          echo "👑 Imperial: ${{ needs.deploy-imperial.result }}"
          echo "🎯 Skill:    ${{ needs.deploy-skill.result }}"
          echo "================================"


