---
title: 'Instrukcje: Wyświetlanie danych za pomocą GridViewRowPresenter'
ms.date: 03/30/2017
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
ms.openlocfilehash: 0e471df3ab6fd10417fc58ece4cdb8ff1c457c95
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59149152"
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a>Instrukcje: Wyświetlanie danych za pomocą GridViewRowPresenter
W tym przykładzie pokazano, jak używać <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów do wyświetlenia danych w kolumnach.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak określić <xref:System.Windows.Controls.GridViewColumnCollection> wyświetlającą <xref:System.DateTime.DayOfWeek%2A> i <xref:System.DateTime.Year%2A> z <xref:System.DateTime> obiektu za pomocą <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów. Przykładzie zdefiniowano też <xref:System.Windows.Style> dla <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](~/samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Controls.GridViewHeaderRowPresenter>
- <xref:System.Windows.Controls.GridViewRowPresenter>
- <xref:System.Windows.Controls.GridViewColumnCollection>
- [GridView — Przegląd](gridview-overview.md)
