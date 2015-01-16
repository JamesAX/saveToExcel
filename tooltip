    initTileTooltip: function (data) {
      var oBundle = this.oBundle;

      // TODO
      /** @type {Grid Layout} [Get overview grid layout] */
      var tileOverview = sap.ui.getCore().byId('overview-custom-tile');
      var tileData = data;
      var tileLists = tileOverview.getContent();

      /** get tile group in one box */
      tileData.forEach(function (tileDataItem, tileListIndex) {
        var tileList = tileLists[tileListIndex].getItems()[1];
        /** get content in the tile box, most of time there are 4 tile boxes */
        var tileboxes = tileList.getItems();
        /** @type {data} [Get corresponding data for one box] */
        var tileboxData = tileDataItem.DATA;
        /** [Go through all tile boxes] */
        tileboxes.forEach(function (tilebox, index) {
          var tileboxDataEach = tileboxData[index];
          var kpiName = tileboxDataEach.KPI_NAME;
          var targetValue = tileboxDataEach.T_VALUE;
          var actualValue = tileboxDataEach.A_VALUE;

          /**	Listen every tile box*/
          $(tilebox.getDomRef()).hover(function (evt) {
            var showtext = '';

            var posotionX = evt.clientX;
            var posotionY = evt.clientY - 90;

            /**	Give every tooltip name, tooltip is the object to store the name*/
            if (sap.tooltip === undefined) {
              sap.tooltip = {};
            }

            /** If no tooltip or enter different tooltip, create a new tooltip*/
            if ($('.tooltip').length === 0 || sap.tooltip.name !==
              tileListIndex + '-' + index) {

              showtext += '<div class="tooltip" style="left:' +
                posotionX + 'px;top:' +
                posotionY + 'px">';
              var tooltipNameText = '<div class="tooltip-name">';
              tooltipNameText += '<p><b>' + oBundle.getText(
                'TooltipKPI') + ':</b></p><br>';
              tooltipNameText += '<p><b>' + oBundle.getText(
                'TooltipActual') + ':</b></p><br>';
              tooltipNameText += '<p><b>' + oBundle.getText(
                'TooltipTarget') + ':</b></p>';
              tooltipNameText += '</div>';

              var tooltipValue = '<div class="tooltip-value">';
              tooltipValue += '<p>' + kpiName + '</p><br>';
              tooltipValue += '<p>' + actualValue + '</p><br>';
              tooltipValue += '<p>' + targetValue + '</p></div>';

              showtext += tooltipNameText + tooltipValue;
              $('body').append(showtext);
            }

            /** Put the name of the new tooltip in tooltip.name*/
            sap.tooltip.name = tileListIndex + '-' + index;

            /** Remove all tooltip except the new one*/
            var length = $('.tooltip').length;
            $('.tooltip').each(function (index, tooltip) {
              if (index !== length - 1) {
                tooltip.remove();
              }
            });

            /** Give the new tooltip listener*/
            $('.tooltip').hover(function (toolEvt) {
              /** If mouse enter tooltip, give the true to ontooltip*/
              sap.ontooltip = true;
            }, function () {
              /** If mouse leave tooltip, give the false to ontooltip*/
              sap.ontooltip = false;
              /** If mouse leave tooltip, Remove all tooltip*/
              $('.tooltip').remove();
            });

          }, function () {
            /** Give time for mouse to enter tooltip before tooltip disappears*/
            ///console.log(sap.ontooltip);
          });

          $('.tile-module').hover(function () {

          }, function () {
            setTimeout(function () {
            	//console.log(sap.ontooltip);
              /** If mouse on tooltip, delete all tooltip except the latest created one*/
              if (sap.ontooltip === false) {
            	  $('.tooltip').remove();
              } else {

              }
            }, 50);
          });



          // tilebox.setTooltip(tooltip);
        });

      });
    },
