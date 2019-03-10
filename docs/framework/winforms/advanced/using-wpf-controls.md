---
title: Korzystanie z formantów WPF
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms Designer [Windows Forms], interoperability with WPF
- interoperability [WPF]
ms.assetid: 03c85dce-26ad-44cd-bc1d-8e0cb56de096
ms.openlocfilehash: 24b88e456628c5a0bdc3cded60b0e52a92057851
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57713803"
---
# <a name="using-wpf-controls"></a>Korzystanie z formantów WPF
W aplikacjach opartych na formularzach Windows, można użyć kontrolek Windows Presentation Foundation (WPF). Mimo że są to dwie technologie inny widok, mogą współdziałać sprawnie.  
  
 Windows Forms Designer udostępnia środowisko projektowania wizualnego do hostowania kontrolki Windows Presentation Foundation. Kontrolki WPF jest hostowana przez kontrolkę Windows Forms specjalne, o nazwie <xref:System.Windows.Forms.Integration.ElementHost>. Ten formant umożliwia formantu WPF do wzięcia udziału w układzie formularza i odbierać komunikaty klawiatury i myszy. W czasie projektowania, można rozmieścić <xref:System.Windows.Forms.Integration.ElementHost> sterować tak samo jak dowolnej kontrolki Windows Forms.  
  
 Umożliwia także kontrolek formularzy Windows Forms w swoich aplikacjach opartego na podsystemie WPF. Aby uzyskać więcej informacji, zobacz [projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Instrukcje: Kopiowanie i wklejanie formantu ElementHost w czasie projektowania](how-to-copy-and-paste-an-elementhost-control-at-design-time.md)  
 Pokazuje, jak kopiowanie kontrolki Windows Presentation Foundation w formularzu Windows.  
  
 [Przewodnik: Rozmieszczanie zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-arranging-wpf-content-on-windows-forms-at-design-time.md)  
 Pokazuje, jak korzystać z funkcji układu formularzy Windows, takich jak Zakotwiczanie i linii przyciągania, aby rozmieścić formanty Windows Presentation Foundation.
  
 [Przewodnik: Tworzenie nowej zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-creating-new-wpf-content-on-windows-forms-at-design-time.md)  
 Pokazuje, jak utworzyć formant programu Windows Presentation Foundation, do użytku w aplikacjach opartych na formularzach Windows.
  
 [Przewodnik: Przypisywanie zawartości WPF na formularzach Windows Forms w czasie projektowania](walkthrough-assigning-wpf-content-on-windows-forms-at-design-time.md)  
 Pokazuje sposób wybierania typów formantów Windows Presentation Foundation, które mają być wyświetlane w formularzu.  
  
 [Przewodnik: Nadawanie stylu zawartości WPF](walkthrough-styling-wpf-content.md)  
 Przedstawia przepływ pracy między Windows Forms Designer i [!INCLUDE[wpfdesigner_current_short](../../../../includes/wpfdesigner-current-short-md.md)] dla stosowanie stylów do kontrolek Windows Presentation Foundation.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.Integration.ElementHost>  
 W tym artykule opisano klasy, które służy do kontrolek Windows Presentation Foundation hosta w swoich aplikacjach opartych na formularzach Windows.  
  
 <xref:System.Windows.Forms.Integration.WindowsFormsHost>  
 W tym artykule opisano klasy, które służy do kontrolek Windows Forms hosta w aplikacji opartej na systemie Windows Presentation Foundation.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Migracja i współdziałanie](../../wpf/advanced/migration-and-interoperability.md)  
 W tym artykule opisano współdziałanie technologii Windows Presentation Foundation i Windows Forms.  
  
 [Projektowanie XAML w programie Visual Studio](/visualstudio/designers/designing-xaml-in-visual-studio)  
 Opisuje sposób projektowania formanty Windows Presentation Foundation w programie Visual Studio.
