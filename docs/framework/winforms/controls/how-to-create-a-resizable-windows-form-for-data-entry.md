---
title: 'Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- TableLayoutPanel control [Windows Forms]
- layout [Windows Forms], resizing
- forms [Windows Forms], creating resizable
- Windows Forms, resizable
ms.assetid: babdf198-404c-485d-a914-ed370c6ecd99
ms.openlocfilehash: a319fba43c6735cd5552dd71d1fb614a6192da97
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45521245"
---
# <a name="how-to-create-a-resizable-windows-form-for-data-entry"></a>Porady: tworzenie formularza systemu Windows o zmiennych rozmiarach do wpisywania danych
Dobre układ odpowiada również zmiany w wymiarach jego formularza nadrzędnego. Możesz użyć <xref:System.Windows.Forms.TableLayoutPanel> kontroli do układu formularza w taki sposób, aby zmienić rozmiar i położenie formantów w spójny sposób zmianami Wymiary formularza. <xref:System.Windows.Forms.TableLayoutPanel> Kontroli jest również przydatne w przypadku gdy zmienia się w zawartości kontrolki Przyczyna zmiany w układzie. Proces omówione w tej procedurze, możesz to zrobić w środowisku Visual Studio.  Zobacz też [wskazówki: Tworzenie formularza Windows o zmiennych rozmiarach dla wpisywania danych](https://msdn.microsoft.com/library/991eahec\(v=vs.110\)).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje sposób użycia <xref:System.Windows.Forms.TableLayoutPanel> kontrolki do tworzenia układu, który odpowiada również, gdy użytkownik zmienia rozmiar formularza. Ilustruje też układ, dobrze reagującego na lokalizację.  
  
 [!code-cpp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/cpp/basicdataentryform.cpp#1)]
 [!code-csharp[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/CS/basicdataentryform.cs#1)]
 [!code-vb[System.Windows.Forms.TableLayoutPanel.DataEntryForm#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.TableLayoutPanel.DataEntryForm/VB/basicdataentryform.vb#1)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Ten przykład wymaga:  
  
-   Odwołania do zestawów systemu, dane systemowe i System.Drawing oraz przestrzeń nazw System.Windows.Forms.  
  
 Aby dowiedzieć się, jak tworzyć aplikacje w tym przykładzie z wiersza polecenia dla języka Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Można także utworzyć tego przykładu w programie Visual Studio, wklejając kod do nowego projektu.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.FlowLayoutPanel>  
 <xref:System.Windows.Forms.TableLayoutPanel>  
 [Instrukcje: zakotwiczenie i dokowanie kontrolek podrzędnych w kontrolce TableLayoutPanel](../../../../docs/framework/winforms/controls/how-to-anchor-and-dock-child-controls-in-a-tablelayoutpanel-control.md)  
 [Instrukcje: projektowanie układu formularzy Windows Forms dobrze reagującego na lokalizację](../../../../docs/framework/winforms/controls/how-to-design-a-windows-forms-layout-that-responds-well-to-localization.md)  
 [Środowisko użytkownika Microsoft Windows, oficjalnych wytycznych dotyczących projektanci i deweloperzy interfejsu użytkownika. Redmond, WA: Microsoft Press, 1999. (USBN: 0-7356-0566-1)](https://www.microsoft.com/mspress/southpacific/books/book11588.htm)
