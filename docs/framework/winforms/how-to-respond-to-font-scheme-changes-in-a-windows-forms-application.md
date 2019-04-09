---
title: 'Instrukcje: Reagowanie na zmiany schematu czcionek w aplikacji Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 85770687ecfad690a251eafec9051c4c20f45dd2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59182107"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Instrukcje: Reagowanie na zmiany schematu czcionek w aplikacji Windows Forms
W systemach operacyjnych Windows użytkownik może zmienić ustawień czcionki systemowe, aby były domyślną czcionkę, są wyświetlane, większy lub mniejszy. Zmiana tych ustawień Czcionka jest krytyczny dla użytkowników, którzy niedowidzących i wymagają większej typu do odczytywania tekstu na swoich ekranach. Można dostosować aplikację Windows Forms, aby reagować na te zmiany przez zwiększenie lub zmniejszenie rozmiaru formularza i wszystkie zawarte tekstu, zawsze wtedy, gdy zmiany schematu czcionek. Jeśli chcesz, aby formularza w taki sposób, aby uwzględnić zmiany w rozmiary czcionek dynamicznie, można dodać kod do formularza.  
  
 Zazwyczaj domyślna czcionka używanych przez formularze Windows jest czcionki zwrócony przez <xref:Microsoft.Win32> wywołanie przestrzeni nazw `GetStockObject(DEFAULT_GUI_FONT)`. Czcionka zwróconych przez to wywołanie zmienia tylko po zmianie rozdzielczość ekranu. Jak pokazano w poniższej procedurze, kod musi zmienić domyślną czcionkę do <xref:System.Drawing.SystemFonts.IconTitleFont%2A> do reagowania na zmiany rozmiaru czcionki.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Użyj czcionki pulpitu i reagować na zmiany schematu czcionek  
  
1.  Tworzenie formularza i dodać kontrolki, które mają do niego. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie aplikacji programu Windows Forms z wiersza polecenia](how-to-create-a-windows-forms-application-from-the-command-line.md) i [kontrolki do użycia w formularzach Windows Forms](./controls/controls-to-use-on-windows-forms.md).  
  
2.  Dodaj odwołanie do <xref:Microsoft.Win32> przestrzeni nazw w kodzie.  
  
     [!code-csharp[WinFormsAutoScaling#2](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  Dodaj następujący kod do konstruktora formularza można dołączyć procedury obsługi zdarzeń wymagane i zmieniać domyślną czcionkę używaną do formularza.  
  
     [!code-csharp[WinFormsAutoScaling#3](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  Implementowanie obsługi dla <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzeń, który powoduje, że formularza w celu automatycznego skalowania podczas <xref:Microsoft.Win32.UserPreferenceCategory.Window> zmian kategorii.  
  
     [!code-csharp[WinFormsAutoScaling#4](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  Na koniec zaimplementować funkcję obsługi <xref:System.Windows.Forms.Form.FormClosing> zdarzenia, które powoduje odłączenie <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> programu obsługi zdarzeń.  
  
     > [!IMPORTANT]
     > Niepodanie tego kodu spowoduje, że aplikacja do wycieku pamięci.  
  
     [!code-csharp[WinFormsAutoScaling#5](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
     [!code-vb[WinFormsAutoScaling#5](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
6.  Skompiluj i uruchom kod.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Aby ręcznie zmienić schematu czcionek w Windows XP  
  
1.  Po uruchomieniu aplikacji Windows Forms kliknij prawym przyciskiem myszy na pulpit Windows i wybierz polecenie **właściwości** z menu skrótów.  
  
2.  W **właściwości wyświetlania** okno dialogowe, kliknij przycisk **wygląd** kartę.  
  
3.  Z **rozmiar czcionki** listy rozwijanej wybierz nowy rozmiar czcionki.  
  
     Można zauważyć, że formularz teraz w przypadku środowiska wykonawczego zmiany schematu czcionek pulpitu. Gdy użytkownik zmieni się między **normalny**, **duży rozmiar czcionki**, i **dodatkowe duży rozmiar czcionki**, formularz zmieni się czcionka i skaluje się poprawnie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[WinFormsAutoScaling#1](~/samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Constructer w tym przykładzie kod zawiera wywołanie `InitializeComponent`, który jest zdefiniowany, tworząc nowy projekt Windows Forms w programie Visual Studio. Usuń ten wiersz kodu, jeśli tworzysz aplikację w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>
- [Automatyczne skalowanie w formularzach systemu Windows](automatic-scaling-in-windows-forms.md)
