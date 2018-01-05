---
title: "Wskazówki: zapewnianie elementów menu standardowego dla formularza"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- menu items [Windows Forms], standard
- toolbars [Windows Forms], walkthroughs
- StatusStrip control [Windows Forms]
- ToolStrip control [Windows Forms]
ms.assetid: dac37d98-589e-4d6d-9673-6437e8943122
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1f1b976a0b5e0962cae155f380b17737077c5353
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="walkthrough-providing-standard-menu-items-to-a-form"></a>Wskazówki: zapewnianie elementów menu standardowego dla formularza
Można zapewnić standardowe menu formularzy z <xref:System.Windows.Forms.MenuStrip> formantu.  
  
 W tym przewodniku przedstawiono sposób użycia <xref:System.Windows.Forms.MenuStrip> formantu, aby utworzyć standardowe menu. Formularz reaguje także po wybraniu elementu menu. Następujące zadania są przedstawione w tym przewodniku:  
  
-   Tworzenie projektu formularzy systemu Windows.  
  
-   Tworzenie menu standardowego.  
  
-   Tworzenie <xref:System.Windows.Forms.StatusStrip> formantu.  
  
-   Obsługa wyboru elementu menu.  
  
 Gdy skończysz, konieczne będzie formularza z standardowe menu, która wyświetla zaznaczenia elementów menu w <xref:System.Windows.Forms.StatusStrip> formantu.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: Podaj standardowe elementy Menu do formularza](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/en-us/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Wystarczających uprawnień, aby można było utworzyć i uruchomić projektów aplikacji formularzy systemu Windows na komputerze, którym [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] jest zainstalowany.  
  
## <a name="creating-the-project"></a>Tworzenie projektu  
 Pierwszym krokiem jest utworzenie projektu i konfigurowanie formularza.  
  
#### <a name="to-create-the-project"></a>Aby utworzyć projekt  
  
1.  Utwórz projekt aplikacji systemu Windows o nazwie **StandardMenuForm**.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Tworzenie projektu aplikacji Windows](http://msdn.microsoft.com/en-us/b2f93fed-c635-4705-8d0e-cf079a264efa).  
  
2.  W narzędziu Projektant dla formularzy systemu Windows wybierz formularza.  
  
## <a name="creating-a-standard-menu"></a>Tworzenie Menu standardowego  
 Projektant formularzy systemu Windows może automatycznie wypełnić <xref:System.Windows.Forms.MenuStrip> kontrolki z elementów menu standardowego.  
  
#### <a name="to-create-a-standard-menu"></a>Aby utworzyć standardowe menu  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.MenuStrip> sterowania do formularza.  
  
2.  Kliknij przycisk <xref:System.Windows.Forms.MenuStrip> kontrolki symbolu tagu (![symbol tagu inteligentnego](../../../../docs/framework/winforms/controls/media/vs-winformsmttagglyph.gif "VS_WinFormSmtTagGlyph")) i wybierz **Wstaw elementy standardowe**.  
  
     <xref:System.Windows.Forms.MenuStrip> Kontroli jest wypełniane przy użyciu elementów menu standardowego.  
  
3.  Kliknij przycisk **pliku** element menu, aby zobaczyć jego elementy menu domyślne i odpowiadające im ikony.  
  
## <a name="creating-a-statusstrip-control"></a>Tworzenie StatusStrip — formant  
 Użyj <xref:System.Windows.Forms.StatusStrip> formantu, aby wyświetlić stan dla aplikacji Windows Forms. W tym przykładzie bieżący wybrane przez użytkownika elementy menu są wyświetlane w <xref:System.Windows.Forms.StatusStrip> formantu.  
  
#### <a name="to-create-a-statusstrip-control"></a>Aby utworzyć StatusStrip — formant  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.StatusStrip> sterowania do formularza.  
  
     <xref:System.Windows.Forms.StatusStrip> Kontroli stacje dokujące automatycznie do dolnej części formularza.  
  
2.  Kliknij przycisk <xref:System.Windows.Forms.StatusStrip> przycisku rozwijanego kontrolki i wybierz **StatusLabel** można dodać <xref:System.Windows.Forms.ToolStripStatusLabel> formant <xref:System.Windows.Forms.StatusStrip> formantu.  
  
## <a name="handling-item-selection"></a>Wybór elementu obsługi  
 Obsługa <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzenia odpowiada po wybraniu elementu menu.  
  
#### <a name="to-handle-item-selection"></a>Do obsługi Zaznaczanie elementów  
  
1.  Kliknij przycisk **pliku** element menu, który został utworzony w tworzenie sekcji standardowe Menu.  
  
2.  W **właściwości** okna, kliknij przycisk **zdarzenia**.  
  
3.  Kliknij dwukrotnie <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.  
  
     Projektant formularzy systemu Windows generuje programu obsługi zdarzeń dla <xref:System.Windows.Forms.ToolStripDropDownItem.DropDownItemClicked> zdarzeń.  
  
4.  Wstaw następujący kod do obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#3)]  
  
5.  Wstaw `UpdateStatus` definicję metody narzędzie do formularza.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StandardMenu#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StandardMenu/VB/Form1.vb#2)]  
  
## <a name="checkpoint"></a>Punkt kontrolny  
  
#### <a name="to-test-your-form"></a>Aby przetestować formularz  
  
1.  Naciśnij klawisz F5, aby skompilować i uruchomić formularza.  
  
2.  Kliknij przycisk **pliku** element menu, aby otworzyć menu.  
  
3.  Na **pliku** menu, kliknij jeden z elementów, aby go wybrać.  
  
     <xref:System.Windows.Forms.StatusStrip> Kontrola Wyświetla wybrany element.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku utworzono formularza standardowe menu. Można użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:  
  
-   Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz [informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki. Aby uzyskać więcej informacji, zobacz [wskazówki: Tworzenie formularza MDI za pomocą scalania Menu i formantami ToolStrip](../../../../docs/framework/winforms/controls/walkthrough-creating-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
-   Nadaj Twojej <xref:System.Windows.Forms.ToolStrip> profesjonalny wygląd kontrolki. Aby uzyskać więcej informacji, zobacz [porady: ustawienie modułu renderowania ToolStrip dla aplikacji](../../../../docs/framework/winforms/controls/how-to-set-the-toolstrip-renderer-for-an-application.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [MenuStrip, kontrolka](../../../../docs/framework/winforms/controls/menustrip-control-windows-forms.md)
