---
title: 'Porady: reagowanie na zmiany schematu czcionek w aplikacji Windows Forms'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Windows Forms, font scheme changes
ms.assetid: 4db27702-22e7-43bf-a07d-9a004549853c
ms.openlocfilehash: 455609ea602f450803718f5be34618b087560d21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33539455"
---
# <a name="how-to-respond-to-font-scheme-changes-in-a-windows-forms-application"></a>Porady: reagowanie na zmiany schematu czcionek w aplikacji Windows Forms
W systemach operacyjnych Windows użytkownik może zmienić ustawienia czcionki systemowe, aby upewnić domyślnej czcionki są wyświetlane, większy lub mniejszy. Zmiana tych ustawień czcionki jest kluczowa dla użytkowników, którzy są niedowidzących i wymagają większej typu tekstu na ekranie. Można dostosować aplikacji Windows Forms reagowanie na te zmiany, zwiększ lub Zmniejsz rozmiar formularza i wszystkich zawartych w niej tekstu przy każdej zmianie schematu czcionek. Jeśli chcesz, aby formularz, aby uwzględnić zmiany w rozmiarze czcionki dynamicznie, można dodać kod do formularza.  
  
 Zazwyczaj domyślnej czcionki używanej przez formularze systemu Windows jest czcionki zwrócony przez <xref:Microsoft.Win32> wywołanie przestrzeni nazw `GetStockObject(DEFAULT_GUI_FONT)`. Czcionki zwróconych przez to połączenie zostanie zmieniona tylko, gdy zmienia się rozdzielczość ekranu. Jak pokazano w poniższej procedurze, kod należy zmienić domyślną czcionkę do <xref:System.Drawing.SystemFonts.IconTitleFont%2A> na odpowiadanie na zmiany w rozmiarze czcionki.  
  
### <a name="to-use-the-desktop-font-and-respond-to-font-scheme-changes"></a>Użyj czcionki pulpitu i reagowanie na zmiany schematu czcionek  
  
1.  Tworzenie formularza i Dodaj formanty, które mają do niej. Aby uzyskać więcej informacji, zobacz [porady: tworzenie aplikacji Windows Forms z wiersza polecenia](../../../docs/framework/winforms/how-to-create-a-windows-forms-application-from-the-command-line.md) i [formanty do użycia w formularzach systemu Windows](../../../docs/framework/winforms/controls/controls-to-use-on-windows-forms.md).  
  
2.  Dodaj odwołanie do <xref:Microsoft.Win32> przestrzeni nazw w kodzie.  
  
     [!code-csharp[WinFormsAutoScaling#2](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#2)]
     [!code-vb[WinFormsAutoScaling#2](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#2)]  
  
3.  Dodaj następujący kod do konstruktora formularza dołączenie obsługi zdarzeń wymagane i zmienić domyślną czcionkę używany dla formularza.  
  
     [!code-csharp[WinFormsAutoScaling#3](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#3)]
     [!code-vb[WinFormsAutoScaling#3](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#3)]  
  
4.  Implementowanie obsługi dla <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> zdarzenie, które powoduje formularza, aby skalować automatycznie po <xref:Microsoft.Win32.UserPreferenceCategory.Window> zmian kategorii.  
  
     [!code-csharp[WinFormsAutoScaling#4](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#4)]
     [!code-vb[WinFormsAutoScaling#4](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#4)]  
  
5.  Na koniec implementuje obsługi dla <xref:System.Windows.Forms.Form.FormClosing> zdarzenie, które odłącza <xref:Microsoft.Win32.SystemEvents.UserPreferenceChanged> obsługi zdarzeń.  
  
> [!IMPORTANT]
>  Nie można dołączyć ten kod spowoduje, że aplikacja do wycieku pamięci.  
  
 [!code-csharp[WinFormsAutoScaling#5](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#5)]
 [!code-vb[WinFormsAutoScaling#5](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#5)]  
  
1.  Kompilowanie i uruchamianie kodu.  
  
### <a name="to-manually-change-the-font-scheme-in-windows-xp"></a>Aby ręcznie zmienić schematu czcionek w systemie Windows XP  
  
1.  Po uruchomieniu aplikacji formularzy systemu Windows kliknij prawym przyciskiem myszy na pulpicie systemu Windows i wybierz polecenie **właściwości** z menu skrótów.  
  
2.  W **właściwości wyświetlania** okno dialogowe, kliknij przycisk **wygląd** kartę.  
  
3.  Z **rozmiar czcionki** listy rozwijanej wybierz nowy rozmiar czcionki.  
  
     Można zauważyć, że formularz teraz reaguje na Uruchom czasu zmiany schematu czcionek pulpitu. Gdy użytkownik zmieni się między **normalny**, **duże czcionki**, i **dodatkowe duże czcionki**, formularz zmiany czcionki i skaluje poprawnie.  
  
## <a name="example"></a>Przykład  
 [!code-csharp[WinFormsAutoScaling#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/WinFormsAutoScaling/CS/Form1.cs#1)]
 [!code-vb[WinFormsAutoScaling#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/WinFormsAutoScaling/VB/Form1.vb#1)]  
  
 Constructer w tym przykładzie kodu zawiera wywołanie `InitializeComponent`, który jest zdefiniowany podczas tworzenia nowego projektu Windows Forms w programie Visual Studio. Usuń ten wiersz kodu, jeśli tworzysz aplikację w wierszu polecenia.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.ContainerControl.PerformAutoScale%2A>  
 [Automatyczne skalowanie w formularzach Windows Forms](../../../docs/framework/winforms/automatic-scaling-in-windows-forms.md)
