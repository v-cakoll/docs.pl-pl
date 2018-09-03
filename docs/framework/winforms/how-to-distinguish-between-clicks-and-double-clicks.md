---
title: 'Porady: rozróżnianie między kliknięciami a dwukrotnymi kliknięciami'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- mouse [Windows Forms], click
- mouse [Windows Forms], double-click
- mouse clicks [Windows Forms], single versus double
ms.assetid: d836ac8c-85bc-4f3a-a761-8aee03dc682c
ms.openlocfilehash: 84d085700091c4e7b8658e8eac4cf86fbd7730d5
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/03/2018
ms.locfileid: "43486493"
---
# <a name="how-to-distinguish-between-clicks-and-double-clicks"></a>Porady: rozróżnianie między kliknięciami a dwukrotnymi kliknięciami
Zazwyczaj pojedynczej *kliknij* inicjuje reakcji interfejsu użytkownika i *kliknij dwukrotnie* rozszerza akcji. Na przykład jednym kliknięciem zwykle wybiera element, a następnie dwukrotne kliknięcie Edytuje wybrany element. Jednak zdarzenia kliknięcia formularze Windows nie łatwe dodawanie scenariusza, w którym przez kliknięcie i kliknij dwukrotnie plik akcje niezgodne, ponieważ akcja powiązany <xref:System.Windows.Forms.Control.Click> lub <xref:System.Windows.Forms.Control.MouseClick> zdarzeń odbywa się przed akcją powiązane <xref:System.Windows.Forms.Control.DoubleClick>lub <xref:System.Windows.Forms.Control.MouseDoubleClick> zdarzeń. W tym temacie przedstawiono dwa rozwiązania tego problemu. Jest jedno rozwiązanie do obsługi zdarzeń kliknij dwukrotnie plik i wycofać akcje w zakresie obsługi zdarzenia click. W rzadkich sytuacjach może być konieczne symulowania kliknij pozycję i kliknij dwukrotnie działanie, obsługując <xref:System.Windows.Forms.Control.MouseDown> zdarzeń i za pomocą <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> i <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A> właściwości <xref:System.Windows.Forms.SystemInformation> klasy. Pomiar czasu między kliknięciami a jeśli drugie kliknięcie występuje przed wartością <xref:System.Windows.Forms.SystemInformation.DoubleClickTime%2A> zostanie osiągnięty, a następnie kliknij przycisk jest w obrębie prostokąta zdefiniowanego przez <xref:System.Windows.Forms.SystemInformation.DoubleClickSize%2A>, wykonania akcji kliknij dwukrotnie plik; w przeciwnym razie wykonania akcji kliknij pozycję.  
  
### <a name="to-roll-back-a-click-action"></a>Aby wycofać akcji kliknij pozycję  
  
-   Sprawdź, czy kontrolka pracujesz z ma standardowy kliknij dwukrotnie działanie. Jeśli nie, Włącz kontrolki z <xref:System.Windows.Forms.Control.SetStyle%2A> metody. Obsłuż zdarzenie kliknij dwukrotnie plik i wycofać kliknij akcję, a także akcji kliknij dwukrotnie plik. Poniższy przykład kodu pokazuje, jak utworzyć niestandardowy przycisk z włączone, a także jak wycofać akcji kliknij w tym przypadku kliknij dwukrotnie plik kodu obsługi dwukrotnego kliknięcia.  
  
     [!code-csharp[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/CS/Form1.cs#1)]
     [!code-vb[System.Windows.Forms.ButtonDoubleClick#1](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ButtonDoubleClick/VB/Form1.vb#1)]  
  
### <a name="to-distinguish-between-clicks-in-the-mousedown-event"></a>Aby rozróżnianie między kliknięciami w MouseDown — zdarzenie  
  
-   Obsługa <xref:System.Windows.Forms.Control.MouseDown> zdarzeń i określić, miejsce i czas span między kliknięciami za pomocą odpowiedniego <xref:System.Windows.Forms.SystemInformation> właściwości i <xref:System.Windows.Forms.Timer> składnika. Wykonaj odpowiednią akcję, zależnie od tego, czy odbywa się kliknij lub kliknij dwukrotnie plik. Poniższy przykład kodu pokazuje, jak można to zrobić.  
  
     [!code-cpp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/cpp/form1.cpp#0)]
     [!code-csharp[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/CS/form1.cs#0)]
     [!code-vb[System.Windows.Forms.SingleVersusDoubleClick#0](../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.SingleVersusDoubleClick/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Kompilowanie kodu  
 Wymagaj tych przykładach:  
  
-   Odwołania do zestawów systemu, System.Drawing i przestrzeń nazw System.Windows.Forms.  
  
 Aby uzyskać informacje o tworzeniu tych przykładów z poziomu wiersza polecenia dla programu Visual Basic lub Visual C#, zobacz [tworzenie z wiersza polecenia](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) lub [wiersza polecenia tworzenia przy użyciu csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Możesz także tworzyć te przykłady w programie Visual Studio, wklejając kod do nowych projektów.  Zobacz też [porady: kompilowanie i uruchamianie pełną Windows Forms kodu przykładzie przy użyciu programu Visual Studio](https://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzanie za pomocą myszy w aplikacjach Windows Forms](../../../docs/framework/winforms/mouse-input-in-a-windows-forms-application.md)
