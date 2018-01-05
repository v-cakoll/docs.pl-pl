---
title: "Korzystanie z formantów WPF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c14da85b377b3ef80d6accbc8b0319959a75bcd5
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="using-wpf-controls"></a>Korzystanie z formantów WPF
Formanty Windows Presentation Foundation (WPF) służy w aplikacjach opartych na formularzach systemu Windows. Chociaż te dwie technologie inny widok, ich współdziałać sprawnie.  
  
 Projektant formularzy systemu Windows udostępnia środowisko wizualnego projektu do hostowania kontrolki Windows Presentation Foundation. Formant WPF jest hostowana przez specjalne formantu formularzy systemu Windows o nazwie <xref:System.Windows.Forms.Integration.ElementHost>. Ten formant umożliwia kontrolce WPF do udziału w układu formularza i odbierać komunikaty klawiatury i myszy. W czasie projektowania, można rozmieścić <xref:System.Windows.Forms.Integration.ElementHost> sterować tak samo jak dowolnej kontrolki formularza systemu Windows.  
  
 Formanty formularzy systemu Windows umożliwia także w aplikacjach opartych na WPF. Aby uzyskać więcej informacji, zobacz [projektanta WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Przedstawia sposób kopiowania formantu Windows Presentation Foundation na formularzu systemu Windows.  
  
 [Przewodnik: rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Przedstawia sposób korzystania z funkcji układ formularzy systemu Windows, takich jak Zakotwiczanie i linie przyciągania, ułożyć kontrolki Windows Presentation Foundation.  
  
 [Przewodnik: zmienianie właściwości hostowanego elementu WPF w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-changing-properties-of-a-hosted-wpf-element-at-design-time.md)  
 Przedstawiono przepływ pracy między Projektant formularzy systemu Windows i [!INCLUDE[wpfdesigner_current_long](../../../../includes/wpfdesigner-current-long-md.md)] zmiany właściwości formantów WPF.  
  
 [Przewodnik: tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Przedstawia sposób tworzenia kontrolki Windows Presentation Foundation, do użycia w aplikacjach opartych na formularzach systemu Windows.  
  
 [Przewodnik: kopiowanie i wklejanie kontrolki ElementHost w oddzielnych formularzach Windows Forms](../../../../docs/framework/winforms/advanced/copy--paste-an-elementhost-control-into-forms.md)  
 Przedstawia sposób kopiowania kontrolki Windows Presentation Foundation z jednego formularza systemu Windows na inny.  
  
 [Przewodnik: przypisywanie zawartości WPF na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Pokazuje, jak wybrać typy formantów systemu Windows Presentation Foundation, które mają być wyświetlane w formularzu.  
  
 [Przewodnik: nadawanie stylu zawartości WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Przedstawiono przepływ pracy między Projektant formularzy systemu Windows i [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] stosowania stylów do kontrolki Windows Presentation Foundation.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 W tym artykule opisano klasy, która służy do kontrolki Windows Presentation Foundation hosta w aplikacjach opartych na formularzach systemu Windows.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 W tym artykule opisano klasy, która służy do hosta formanty formularzy systemu Windows w aplikacji opartej na systemie Windows Presentation Foundation.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 Opisuje współdziałanie między technologii Windows Presentation Foundation i formularze systemu Windows.  
  
 [Projektant WPF](http://msdn.microsoft.com/en-us/c6c65214-8411-4e16-b254-163ed4099c26)  
 Opisuje sposób projektowania kontrolek Windows Presentation Foundation w [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)].
