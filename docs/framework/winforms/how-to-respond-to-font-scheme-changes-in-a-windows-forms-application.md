---
title: Reagowanie na zmiany schematu czcionek w aplikacji Windows Forms
titleSuffix: ''
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: e3b96139a7cfd4b268d81b1da58229527e2beb87
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76739230"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Porady: reagowanie na zmiany schematu czcionek w aplikacji Windows Forms
W systemach operacyjnych Windows, użytkownik może zmienić ustawienia czcionek dla całego systemu, aby czcionka domyślna była większa lub mniejsza. Zmiana tych ustawień czcionki jest niezwykle ważna dla użytkowników, którzy są wizualnie niepełnosprawni i wymagają większego typu w celu odczytania tekstu na ekranie. Możesz dostosować aplikację Windows Forms, aby reagować na te zmiany, zwiększając lub zmniejszając rozmiar formularza i cały tekst zawarty po każdym zmianie schematu czcionek. Jeśli chcesz, aby formularz dynamicznie mieścił zmiany rozmiarów czcionek, możesz dodać kod do formularza.  
  
 Zazwyczaj domyślną czcionką używaną przez Windows Forms jest czcionka zwrócona przez wywołanie przestrzeni nazw <xref:Microsoft.Win32> do `GetStockObject(DEFAULT_GUI_FONT)`. Czcionka zwracana przez to wywołanie zmienia się tylko wtedy, gdy zmienia się rozdzielczość ekranu. Jak pokazano w poniższej procedurze, kod musi zmienić czcionkę domyślną, aby <xref:System.Drawing.SystemFonts.IconTitleFont%2A>, aby odpowiadały na zmiany rozmiaru czcionki.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Aby używać czcionki pulpitu i odpowiadać na zmiany schematu czcionek  
  
1. Utwórz formularz i Dodaj do niego formanty. Aby uzyskać więcej informacji, zobacz [How to: Create a Windows Forms Application z wiersza polecenia](how-to-create-a-windows-forms-application-from-the-command-line.md) i [formantów, które mają być używane w Windows Forms](./controls/controls-to-use-on-windows-forms.md).  
  
2. Dodaj odwołanie do przestrzeni nazw <xref:Microsoft.Win32> do kodu.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3. Dodaj następujący kod do konstruktora formularza, aby podłączyć wymagane programy obsługi zdarzeń i zmienić domyślną czcionkę używaną dla formularza.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4. Zaimplementuj procedurę obsługi dla zdarzenia <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>, które powoduje automatyczne skalowanie formularza po zmianie kategorii <xref:Microsoft.Win32.UserPreferenceCategory.Window>.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5. Na koniec Zaimplementuj procedurę obsługi dla zdarzenia <xref:System.Windows.Forms.Form.FormClosing>, które odłącza procedurę obsługi zdarzeń <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged>.  
  
     > [!IMPORTANT]
     > Niepowodzenie dołączenia tego kodu spowoduje przeciek pamięci przez aplikację.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6. Kompiluj i uruchamiaj kod.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Aby ręcznie zmienić schemat czcionek w systemie Windows XP  
  
1. Gdy aplikacja Windows Forms jest uruchomiona, kliknij prawym przyciskiem myszy pulpit systemu Windows i wybierz polecenie **Właściwości** z menu skrótów.  
  
2. W oknie dialogowym **właściwości wyświetlania** kliknij kartę **wygląd** .  
  
3. W polu listy rozwijanej **rozmiar czcionki** wybierz nowy rozmiar czcionki.  
  
     Zobaczysz, że formularz teraz reaguje na zmiany w czasie wykonywania w schemacie czcionek pulpitu. Gdy użytkownik zmieni się między **normalną**, **dużą czcionką**i **bardzo dużą**czcionką, formularz zmienia czcionkę i skaluje się poprawnie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Konstruktor w tym przykładzie kodu zawiera wywołanie do `InitializeComponent`, który jest definiowany podczas tworzenia nowego projektu Windows Forms w programie Visual Studio. Usuń ten wiersz kodu, jeśli tworzysz aplikację w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Automatyczne skalowanie w formularzach Windows Forms](automatic-scaling-in-windows-forms.md)
