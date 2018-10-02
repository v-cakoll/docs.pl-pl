---
title: Korzystanie z formantów WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: be925bdceea3dd01c568d85fe025d6e037066454
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2018
ms.locfileid: "47459662"
---
# <a name="using-wpf-controls"></a>Korzystanie z formantów WPF
W aplikacjach opartych na formularzach Windows, można użyć kontrolek Windows Presentation Foundation (WPF). Mimo że są to dwie technologie inny widok, mogą współdziałać sprawnie.  
  
 Windows Forms Designer udostępnia środowisko projektowania wizualnego do hostowania kontrolki Windows Presentation Foundation. Kontrolki WPF jest hostowana przez kontrolkę Windows Forms specjalne, o nazwie <xref:System.Windows.Forms.Integration.ElementHost>. Ten formant umożliwia formantu WPF do wzięcia udziału w układzie formularza i odbierać komunikaty klawiatury i myszy. W czasie projektowania, można rozmieścić <xref:System.Windows.Forms.Integration.ElementHost> sterować tak samo jak dowolnej kontrolki Windows Forms.  
  
 Umożliwia także kontrolek formularzy Windows Forms w swoich aplikacjach opartego na podsystemie WPF. Aby uzyskać więcej informacji, zobacz [projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: kopiowanie i wklejanie kontrolki ElementHost w czasie projektowania](../../../../docs/framework/winforms/advanced/how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Pokazuje, jak kopiowanie kontrolki Windows Presentation Foundation w formularzu Windows.  
  
 [Przewodnik: rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Pokazuje, jak korzystać z funkcji układu formularzy Windows, takich jak Zakotwiczanie i linii przyciągania, aby rozmieścić formanty Windows Presentation Foundation.
  
 [Przewodnik: tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Pokazuje, jak utworzyć formant programu Windows Presentation Foundation, do użytku w aplikacjach opartych na formularzach Windows.
  
 [Przewodnik: przypisywanie zawartości WPF na formularzach Windows Forms w czasie projektowania](../../../../docs/framework/winforms/advanced/walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Pokazuje sposób wybierania typów formantów Windows Presentation Foundation, które mają być wyświetlane w formularzu.  
  
 [Przewodnik: nadawanie stylu zawartości WPF](../../../../docs/framework/winforms/advanced/walkthrough-styling-wpf-content.md)  
 Przedstawia przepływ pracy między Windows Forms Designer i [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] dla stosowanie stylów do kontrolek Windows Presentation Foundation.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 W tym artykule opisano klasy, które służy do kontrolek Windows Presentation Foundation hosta w swoich aplikacjach opartych na formularzach Windows.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 W tym artykule opisano klasy, które służy do kontrolek Windows Forms hosta w aplikacji opartej na systemie Windows Presentation Foundation.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Migracja i współdziałanie](../../../../docs/framework/wpf/advanced/migration-and-interoperability.md)  
 W tym artykule opisano współdziałanie technologii Windows Presentation Foundation i Windows Forms.  
  
 [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 Opisuje sposób projektowania formanty Windows Presentation Foundation w programie Visual Studio.
