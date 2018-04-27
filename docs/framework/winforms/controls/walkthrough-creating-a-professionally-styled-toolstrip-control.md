---
title: 'Wskazówki: tworzenie profesjonalnego formantu ToolStrip'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ToolStripProfessionalRenderer class [Windows Forms]
- ToolStripRenderer class [Windows Forms]
- toolbars [Windows Forms], walkthroughs
- ToolStrip control [Windows Forms], creating professionally styled controls
ms.assetid: b52339ae-f1d3-494e-996e-eb455614098a
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 18ffb09e581b830329a0d32f11ae09d8b0f68788
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/27/2018
---
# <a name="walkthrough-creating-a-professionally-styled-toolstrip-control"></a>Wskazówki: tworzenie profesjonalnego formantu ToolStrip
Umożliwia aplikacji <xref:System.Windows.Forms.ToolStrip> określa profesjonalny wygląd i zachowanie, tworząc własne klasy pochodzące z <xref:System.Windows.Forms.ToolStripProfessionalRenderer> typu.  
  
 W tym przewodniku przedstawiono sposób użycia <xref:System.Windows.Forms.ToolStrip> służy do tworzenia złożonych kontrolek, podobny **okienka nawigacji** udostępniane przez Microsoft Outlook®. Następujące zadania są przedstawione w tym przewodniku:  
  
-   Tworzenie projektu Biblioteka formantów systemu Windows.  
  
-   Projektowania formantu StackView.  
  
-   Implementowanie niestandardowego modułu renderowania.  
  
 Gdy skończysz, konieczne będzie formantu do ponownego użycia niestandardowego klienta o profesjonalny wygląd formantu Microsoft Office® XP.  
  
 Aby skopiować kod w tym temacie na jednej liście, zobacz [porady: tworzenie profesjonalnego styl formantu ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-a-professionally-styled-toolstrip-control.md).  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
## <a name="prerequisites"></a>Wymagania wstępne  
 W celu przeprowadzenia tego instruktażu potrzebne są:  
  
-   Wystarczających uprawnień, aby mieć możliwość tworzenia i uruchamiania projektów aplikacji formularzy systemu Windows na komputerze, którym jest zainstalowany program Visual Studio.  
  
## <a name="creating-a-windows-control-library-project"></a>Tworzenie projektu biblioteki sterowania systemu Windows  
 Pierwszym krokiem jest do tworzenia projektu biblioteki formantu.  
  
#### <a name="to-create-the-control-library-project"></a>Aby utworzyć projekt z kontroli biblioteki  
  
1.  Utwórz nowy projekt Biblioteka formantów systemu Windows o nazwie `StackViewLibrary`.  
  
2.  W **Eksploratora rozwiązań**, usuń formant domyślnego projektu przez usunięcie pliku źródłowego o nazwie "UserControl1.cs" lub "UserControl1.vb", w zależności od języka wybór.  
  
     Aby uzyskać więcej informacji, zobacz [NIB: porady: usuwanie, usuwania i wykluczanie elementów](http://msdn.microsoft.com/library/6dffdc86-29c8-4eff-bcd8-e3a0dd9e9a73).  
  
3.  Dodaj nową <xref:System.Windows.Forms.UserControl> elementu do **StackViewLibrary** projektu. Nadaj nazwę podstawową nowy plik źródłowy `StackView`.  
  
## <a name="designing-the-stackview-control"></a>Projektowania formantu StackView  
 `StackView` Formant jest formantu złożonego za pomocą jeden element podrzędny <xref:System.Windows.Forms.ToolStrip> formantu. Aby uzyskać więcej informacji na temat formanty złożone, zobacz [odmian Kontrolki niestandardowe](../../../../docs/framework/winforms/controls/varieties-of-custom-controls.md).  
  
#### <a name="to-design-the-stackview-control"></a>Projekt kontroli StackView  
  
1.  Z **przybornika**, przeciągnij <xref:System.Windows.Forms.ToolStrip> sterowania na powierzchnię projektu.  
  
2.  W **właściwości** ustaw <xref:System.Windows.Forms.ToolStrip> właściwości formantu zgodnie z poniższą tabelą.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Nazwa|`stackStrip`|  
    |CanOverflow|`false`|  
    |Doku.|<xref:System.Windows.Forms.DockStyle.Bottom>|  
    |Czcionki|`Tahoma, 10pt, style=Bold`|  
    |GripStyle|<xref:System.Windows.Forms.ToolStripGripStyle.Hidden>|  
    |LayoutStyle|<xref:System.Windows.Forms.ToolStripLayoutStyle.VerticalStackWithOverflow>|  
    |Dopełnienie|`0, 7, 0, 0`|  
    |RenderMode|<xref:System.Windows.Forms.ToolStripRenderMode.Professional>|  
  
3.  W narzędziu Projektant dla formularzy systemu Windows, kliknij przycisk <xref:System.Windows.Forms.ToolStrip> formantu **Dodaj** przycisk i dodać <xref:System.Windows.Forms.ToolStripButton> do `stackStrip` formantu.  
  
4.  W **właściwości** ustaw <xref:System.Windows.Forms.ToolStripButton> właściwości formantu zgodnie z poniższą tabelą.  
  
    |Właściwość|Wartość|  
    |--------------|-----------|  
    |Nazwa|`mailStackButton`|  
    |CheckOnClick|true|  
    |CheckState|<xref:System.Windows.Forms.CheckState.Checked>|  
    |DisplayStyle|<xref:System.Windows.Forms.ToolStripItemDisplayStyle.ImageAndText>|  
    |ImageAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
    |ImageScaling|<xref:System.Windows.Forms.ToolStripItemImageScaling.None>|  
    |ImageTransparentColor|`238, 238, 238`|  
    |Margines|`0, 0, 0, 0`|  
    |Dopełnienie|`3, 3, 3, 3`|  
    |Tekst|**Poczty**|  
    |TextAlign|<xref:System.Drawing.ContentAlignment.MiddleLeft>|  
  
5.  Powtórz kroki od 7 do trzech więcej <xref:System.Windows.Forms.ToolStripButton> kontrolki.  
  
     Nazwa kontrolki `calendarStackButton`, `contactsStackButton`, i `tasksStackButton`. Ustaw wartość <xref:System.Windows.Forms.Control.Text%2A> właściwości **kalendarza**, **kontaktów**, i **zadania**odpowiednio.  
  
## <a name="handling-events"></a>Obsługa zdarzeń  
 Dwa zdarzenia są ważne dla zapewnienia `StackView` kontroli zadziała poprawnie. Obsługa <xref:System.Windows.Forms.UserControl.Load> zdarzenie, aby poprawnie pozycji formantu. Obsługa <xref:System.Windows.Forms.ToolStripItem.Click> zdarzeń dla każdego <xref:System.Windows.Forms.ToolStripButton> umożliwiają `StackView` kontrolowania podobne do zachowania stanu <xref:System.Windows.Forms.RadioButton> kontroli.  
  
#### <a name="to-handle-events"></a>Do obsługi zdarzeń  
  
1.  W narzędziu Projektant dla formularzy systemu Windows wybierz `StackView` formantu.  
  
2.  W **właściwości** okna, kliknij przycisk **zdarzenia**.  
  
3.  Kliknij dwukrotnie zdarzenie obciążenia, aby wygenerować `StackView_Load` obsługi zdarzeń.  
  
4.  W `StackView_Load` program obsługi zdarzeń, skopiuj i wklej poniższy kod.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#3)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#3)]  
  
5.  W narzędziu Projektant dla formularzy systemu Windows wybierz `mailStackButton` formantu.  
  
6.  W **właściwości** okna, kliknij przycisk **zdarzenia**.  
  
7.  Kliknij dwukrotnie zdarzenie Click.  
  
     Projektant formularzy systemu Windows generuje `mailStackButton_Click` obsługi zdarzeń.  
  
8.  Zmień nazwę `mailStackButton_Click` program obsługi zdarzeń do `stackButton_Click`.  
  
     Aby uzyskać więcej informacji, zobacz [porady: Zmienianie nazwy identyfikator (Visual Basic)](http://msdn.microsoft.com/library/e5a5edf8-3dba-4119-81f4-fc2aba180e0c).  
  
9. Wstaw następujący kod do `stackButton_Click` obsługi zdarzeń.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#4)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#4](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#4)]  
  
10. W narzędziu Projektant dla formularzy systemu Windows wybierz `calendarStackButton` formantu.  
  
11. W **właściwości** oknie ustawioną zdarzenie Click `stackButton_Click` obsługi zdarzeń.  
  
12. Powtórz kroki od 10 i 11 dla `contactsStackButton` i `tasksStackButton` kontrolki.  
  
## <a name="defining-icons"></a>Definiowanie ikon  
 Każdy `StackView` przycisk ma skojarzona ikona. Dla wygody, każda z ikon jest reprezentowany jako ciąg zakodowany w formacie Base64, którego deserializowany jest przed <xref:System.Drawing.Bitmap> jest tworzony z niego. W środowisku produkcyjnym przechowują dane mapy bitowej jako zasób i ikony wyświetlane w narzędziu Projektant dla formularzy systemu Windows. Aby uzyskać więcej informacji, zobacz [porady: Dodawanie obrazy tła do formularzy systemu Windows](http://msdn.microsoft.com/library/7a509ba2-055c-4ae6-b88a-54625c6d9aff).  
  
#### <a name="to-define-icons"></a>Aby zdefiniować ikon  
  
1.  W edytorze kodu Wstaw następujący kod do `StackView` definicji klasy. Ten kod inicjuje bitmap do <xref:System.Windows.Forms.ToolStripButton> ikon.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#2)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#2](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#2)]  
  
2.  Dodaj wywołanie do `InitializeImages` metoda `StackView` konstruktora klasy.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="implementing-a-custom-renderer"></a>Implementowanie niestandardowego modułu renderowania  
 Można dostosować większość elementów `StackView` kontrolować Moje Implementacja klasy, która jest pochodną <xref:System.Windows.Forms.ToolStripRenderer> klasy. W tej procedurze zostaną zaimplementowane <xref:System.Windows.Forms.ToolStripProfessionalRenderer> klasy, która dostosowuje uchwytu i rysuje gradientu tła <xref:System.Windows.Forms.ToolStripButton> kontrolki.  
  
#### <a name="to-implement-a-custom-renderer"></a>Aby zaimplementować niestandardowego modułu renderowania  
  
1.  Wstaw następujący kod do `StackView` kontrolować definicji.  
  
     Jest to definicja `StackRenderer` klasy, co zastępuje <xref:System.Windows.Forms.ToolStripRenderer.RenderGrip>, <xref:System.Windows.Forms.ToolStripRenderer.RenderToolStripBorder>, i <xref:System.Windows.Forms.ToolStripRenderer.RenderButtonBackground> metody do tworzenia niestandardowych wyglądu.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#10)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#10)]  
  
2.  W `StackView` konstruktora formantu, Utwórz nowe wystąpienie klasy `StackRenderer` klasy i przypisz tego wystąpienia `stackStrip` formantu <xref:System.Windows.Forms.ToolStrip.Renderer%2A> właściwości.  
  
     [!code-csharp[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/CS/StackView.cs#5)]
     [!code-vb[System.Windows.Forms.ToolStrip.StackView#5](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ToolStrip.StackView/VB/StackView.vb#5)]  
  
## <a name="testing-the-stackview-control"></a>Testowanie formantu StackView  
 `StackView` Formant pochodzi z <xref:System.Windows.Forms.UserControl> klasy. W związku z tym można przetestować kontrolki z **kontenera testu UserControl**. Aby uzyskać więcej informacji, zobacz [porady: testowanie zachowania UserControl w czasie wykonywania](../../../../docs/framework/winforms/controls/how-to-test-the-run-time-behavior-of-a-usercontrol.md).  
  
#### <a name="to-test-the-stackview-control"></a>Aby sprawdzić formant StackView  
  
1.  Naciśnij klawisz F5, aby skompilować projekt i uruchomić **kontener testu UserControl**.  
  
2.  Przesuń wskaźnik myszy nad przycisków `StackView` kontroli, a następnie kliknij przycisk, aby zobaczyć wygląd stan zaznaczenia.  
  
## <a name="next-steps"></a>Następne kroki  
 W tym przewodniku utworzono kontrolki do ponownego użycia niestandardowego klienta profesjonalny wygląd formantu pakietu Office XP. Można użyć <xref:System.Windows.Forms.ToolStrip> rodziny formantów do innych celów:  
  
-   Tworzenie menu skrótów dla formantów z <xref:System.Windows.Forms.ContextMenuStrip>. Aby uzyskać więcej informacji, zobacz [informacje o składniku ContextMenu](../../../../docs/framework/winforms/controls/contextmenu-component-overview-windows-forms.md).  
  
-   Tworzenie formularza z menu standardowego automatycznie wypełnione. Aby uzyskać więcej informacji, zobacz [wskazówki: zapewnianie standardowe elementy Menu do formularza](../../../../docs/framework/winforms/controls/walkthrough-providing-standard-menu-items-to-a-form.md).  
  
-   Tworzenie wielu formularza interfejsu (MDI) dokumentu z dokowanie <xref:System.Windows.Forms.ToolStrip> kontrolki. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie formularza MDI za pomocą scalania Menu i formantów ToolStrip](../../../../docs/framework/winforms/controls/how-to-create-an-mdi-form-with-menu-merging-and-toolstrip-controls.md).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.MenuStrip>  
 <xref:System.Windows.Forms.ToolStrip>  
 <xref:System.Windows.Forms.StatusStrip>  
 [ToolStrip, kontrolka](../../../../docs/framework/winforms/controls/toolstrip-control-windows-forms.md)  
 [Instrukcje: zapewnianie elementów menu standardowego dla formularza](../../../../docs/framework/winforms/controls/how-to-provide-standard-menu-items-to-a-form.md)
