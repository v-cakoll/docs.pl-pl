---
title: "Porady: wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- DataRepeater, data-binding
- DataRepeater, displaying bound controls
ms.assetid: 56a15326-1334-4275-af4e-075cad79e6f7
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 770003c8879661bfc1ce683f5b6ed84483cf47ea
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-display-bound-data-in-a-datarepeater-control-visual-studio"></a>Porady: wyświetlanie powiązanych danych w formancie DataRepeater (Visual Studio)
Najczęściej używane <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> sterowania są wyświetlane powiązane dane z bazy danych lub inne źródła danych.  
  
 Oprócz formanty powiązane, można dodać inne formanty, takie jak statyczną etykietę lub obraz jest powtarzany na każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu. Aby uzyskać więcej informacji, zobacz [porady: wyświetlanie formantów niepowiązanych w formancie Datarepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md).  
  
 Można także powiązać ze źródłem danych w czasie wykonywania przez ustawienie <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.VirtualMode%2A> właściwości `True` i przypisywanie źródło danych do <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater.DataSource%2A> właściwości. W takim przypadku należy zarządzać wszystkie interakcje ze źródłem danych. Aby uzyskać więcej informacji, zobacz [tryb wirtualny w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/virtual-mode-in-the-datarepeater-control-visual-studio.md).  
  
[!INCLUDE[note_settings_general](~/includes/note-settings-general-md.md)]  
  
### <a name="to-create-a-data-bound-datarepeater"></a>Aby utworzyć DataRepeater powiązane z danymi  
  
1.  Przeciągnij <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> kontrolować z **Visual Basic PowerPacks** karcie **przybornika** formularza lub kontenera formantu.  
  
2.  Przeciągnij uchwyt zmiany rozmiaru i pozycji do rozmiaru i pozycji formantu.  
  
     Należy pamiętać, że kontrolka ma dwóch regionach prostokątny. Górny obszar jest *szablon elementu*; formanty dodawane do szablonu zostanie powtórzona w każdej pozycji w <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu w czasie wykonywania. Niższe region jest *okienka ekranu*, której elementy będą wyświetlane.  
  
     Można również rozmiaru i pozycji formant lub szablon elementu zmieniając **rozmiar** i **pozycji** właściwości w oknie właściwości.  
  
3.  Na **danych** menu, kliknij przycisk **Pokaż źródeł danych**.  
  
    > [!NOTE]
    >  Jeśli **źródeł danych** okna jest pusta, Dodaj źródło danych do niej. Aby uzyskać więcej informacji, zobacz [Dodawanie nowych źródeł danych](/visualstudio/data-tools/add-new-data-sources).  
  
4.  W **źródeł danych** okna, wybierz węzeł najwyższego poziomu dla tabeli, która zawiera dane, które chcesz powiązać.  
  
5.  Zmień typ docelowej tabeli `Details` klikając `Details` na liście rozwijanej na węźle tabeli.  
  
6.  Wybierz węzeł tabeli i przeciągnij go na region szablonu elementu <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater> formantu.  
  
     Można określić, jakie typy formantów są wyświetlane dla każdego pola. Aby uzyskać więcej informacji, zobacz [Ustawianie formantu do utworzenia podczas przeciągania z okna źródeł danych](/visualstudio/data-tools/set-the-control-to-be-created-when-dragging-from-the-data-sources-window).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:Microsoft.VisualBasic.PowerPacks.DataRepeater>  
 [Wprowadzenie do formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/introduction-to-the-datarepeater-control-visual-studio.md)  
 [Porady: wyświetlanie formantów niepowiązanych w formancie DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-display-unbound-controls-in-a-datarepeater-control-visual-studio.md)  
 [Porady: Tworzenie formularza wzorzec/szczegół za pomocą dwóch formantów DataRepeater (Visual Studio)](../../../visual-basic/developing-apps/windows-forms/how-to-create-a-master-detail-form-by-using-two-datarepeater-controls.md)  
 [Porady: Zmienianie wyglądu formantu DataRepeater](../../../visual-basic/developing-apps/windows-forms/how-to-change-the-appearance-of-a-datarepeater-control-visual-studio.md)  
 [Rozwiązywanie problemów z formantem DataRepeater](../../../visual-basic/developing-apps/windows-forms/troubleshooting-the-datarepeater-control-visual-studio.md)
