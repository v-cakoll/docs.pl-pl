---
title: "Porady: Ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ToolStripMenuItems [Windows Forms], hiding menu items in designer
- MenuStrip control [Windows Forms], hiding menu items in designer
- menu items [Windows Forms], hiding
ms.assetid: 8f1b057e-3d8a-4f11-88df-935f7b29a836
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 06a95581e156a7027c8fa0bda6e5fbc4babdb85b
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/19/2018
---
# <a name="how-to-hide-toolstripmenuitems-using-the-designer"></a>Porady: Ukrywanie ToolStripMenuItems przy użyciu narzędzia Projektant
Ukrywanie elementów menu jest możliwość sterowania interfejsem użytkownika (UI), aplikacji i ograniczyć poleceń użytkownika. Często chcesz ukryć całe menu, gdy wszystkich elementów menu na nim są niedostępne. Przedstawia informacje o tym przeszkadzał dla użytkownika. Ponadto możesz chcieć zarówno Ukryj i Wyłącz menu lub elementu menu, jak ukrywanie wyłącznie nie uniemożliwia użytkownikowi uzyskiwanie dostępu do polecenia menu za pomocą klawisza skrótu. Aby uzyskać więcej informacji dotyczących wyłączanie elementów menu, zobacz [porady: wyłączanie ToolStripMenuItems przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-hide-a-top-level-menu-and-its-submenu-items"></a>Aby ukryć menu najwyższego poziomu i jego podmenu  
  
1.  Wybierz element menu najwyższego poziomu i ustaw jej <xref:System.Windows.Forms.ToolStripItem.Visible%2A> lub <xref:System.Windows.Forms.ToolStripItem.Available%2A> właściwości `false`.  
  
     Ukrycie element menu najwyższego poziomu, również są ukryte wszystkich elementów menu w ramach danego menu. Jeśli klikniesz w innym miejscu niż na <xref:System.Windows.Forms.MenuStrip> po ustawieniu <xref:System.Windows.Forms.ToolStripItem.Visible%2A> do `false`, element menu najwyższego poziomu całego i jego podmenu elementy są usuwane z formularza, w związku z tym przedstawiający efekt czasu wykonywania akcji. Aby wyświetlić element menu najwyższego poziomu ukryte w czasie projektowania, kliknij <xref:System.Windows.Forms.MenuStrip> w **zasobnik składnika**w **konspekt dokumentu**, lub w górnej części siatki właściwości.  
  
> [!NOTE]
>  Rzadko spowoduje ukrycie całe menu z wyjątkiem wielu menu podrzędne interfejsu (MDI) dokumentu w scenariuszu scalania.  
  
### <a name="to-hide-a-submenu-item"></a>Aby ukryć element podmenu  
  
1.  Wybierz element podmenu i ustaw jej <xref:System.Windows.Forms.ToolStripItem.Visible%2A> właściwości `false`.  
  
     Ukrycie elementu podmenu pozostaje widoczne w formularzu w czasie projektowania, aby można go łatwo wybrać dalszej pracy. Będzie ona faktycznie ukryta w czasie wykonywania.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ToolStripItem.Visible%2A>  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Enabled%2A>  
 <xref:System.Windows.Forms.ToolStripItem.Available%2A>  
 <xref:System.Windows.Forms.ToolStripMenuItem.Overflow%2A>  
 [MenuStrip, kontrolka — omówienie](../../../../docs/framework/winforms/controls/menustrip-control-overview-windows-forms.md)  
 [Instrukcje: wyłączanie kontrolki ToolStripMenuItems przy użyciu narzędzia Projektant](../../../../docs/framework/winforms/controls/how-to-disable-toolstripmenuitems-using-the-designer.md)
