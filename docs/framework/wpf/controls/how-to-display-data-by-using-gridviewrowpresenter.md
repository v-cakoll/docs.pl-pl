---
title: "Jak wyświetlić dane za pomocą GridViewRowPresenter"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- displaying data with GridViewRowPresenter [WPF]
- GridViewRowPresenter [WPF]
ms.assetid: bdb785a5-a262-44d5-a517-ea14383e5f70
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ebe0a47d38a2cfda2a7d150b4a3886d9f63ee190
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-data-by-using-gridviewrowpresenter"></a>Jak wyświetlić dane za pomocą GridViewRowPresenter
Ten przykład przedstawia sposób użycia <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów do wyświetlenia danych w kolumnach.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób określić <xref:System.Windows.Controls.GridViewColumnCollection> wyświetlający <xref:System.DateTime.DayOfWeek%2A> i <xref:System.DateTime.Year%2A> z <xref:System.DateTime> obiektu za pomocą <xref:System.Windows.Controls.GridViewRowPresenter> i <xref:System.Windows.Controls.GridViewHeaderRowPresenter> obiektów. Definiuje również przykładzie <xref:System.Windows.Style> dla <xref:System.Windows.Controls.GridViewColumn.Header%2A> z <xref:System.Windows.Controls.GridViewColumn>.  
  
 [!code-xaml[GridViewRowPresenterSample#GridViewRowPresenter](../../../../samples/snippets/csharp/VS_Snippets_Wpf/GridViewRowPresenterSample/CS/Window1.xaml#gridviewrowpresenter)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Controls.GridViewHeaderRowPresenter>  
 <xref:System.Windows.Controls.GridViewRowPresenter>  
 <xref:System.Windows.Controls.GridViewColumnCollection>  
 [Omówienie widoku GridView](../../../../docs/framework/wpf/controls/gridview-overview.md)
