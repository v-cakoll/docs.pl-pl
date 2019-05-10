---
title: 'Instrukcje: Stosowanie modyfikatorów i właściwości „GenerateMember"'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
f1_keywords:
- Designer_GenerateMember
- Designer_Modifiers
helpviewer_keywords:
- base forms
- inheritance [Windows Forms], forms
- inherited forms [Windows Forms], Windows Forms
- inherited forms
- form inheritance
- Windows Forms, inheritance
ms.assetid: 3381a5e4-e1a3-44e2-a765-a0b758937b85
ms.openlocfilehash: 3fbaaae53aa60f6356c3a8daa0513de86ef2dacb
ms.sourcegitcommit: 0d0a6e96737dfe24d3257b7c94f25d9500f383ea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2019
ms.locfileid: "65211297"
---
# <a name="how-to-use-the-modifiers-and-generatemember-properties"></a>Instrukcje: Stosowanie modyfikatorów i właściwości „GenerateMember"

Po umieszczeniu składnika w formularzu Windows dwie właściwości są dostarczane przez środowisko projektowania: `GenerateMember` i `Modifiers`. `GenerateMember` Właściwość określa, kiedy Windows Forms Designer generuje zmienną składową dla składnika. `Modifiers` Właściwość jest modyfikator dostępu przypisane do tej zmiennej elementu członkowskiego. Jeśli wartość `GenerateMember` właściwość `false`, wartość `Modifiers` właściwość nie ma wpływu.

## <a name="specify-whether-a-component-is-a-member-of-the-form"></a>Określ, czy składnik jest elementem członkowskim formularza

1. W programie Windows Forms Designer w programie Visual Studio Otwórz formularz.

2. Otwórz **przybornika**i w formularzu, należy umieścić trzy <xref:System.Windows.Forms.Button> kontrolki.

3. Ustaw `GenerateMember` i `Modifiers` właściwości dla każdego <xref:System.Windows.Forms.Button> kontroli zgodnie z poniższą tabelą.

    |Nazwa przycisku|Wartość GenerateMember|Wartość modyfikatorów|
    |-----------------|--------------------------|---------------------|
    |`button1`|`true`|`private`|
    |`button2`|`true`|`protected`|
    |`button3`|`false`|Nie wprowadzono zmian|

4. Skompiluj rozwiązanie.

5. W **Eksploratora rozwiązań**, kliknij przycisk **Pokaż wszystkie pliki** przycisku.

6. Otwórz **Form1** węzła, a następnie w **Edytor kodu**, otwórz **Form1.Designer.vb** lub **Form1.Designer.cs** pliku. Ten plik zawiera kod wyemitowane przez Windows Forms Designer.

7. Znajdź deklaracje dla trzech przycisków. Poniższy przykład kodu pokazuje różnice określony przez `GenerateMember` i `Modifiers` właściwości.

     [!code-csharp[System.Windows.Forms.GenerateMember#3](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#3)]
     [!code-vb[System.Windows.Forms.GenerateMember#3](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#3)]

     [!code-csharp[System.Windows.Forms.GenerateMember#2](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/CS/Form1.cs#2)]
     [!code-vb[System.Windows.Forms.GenerateMember#2](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.GenerateMember/VB/Form1.vb#2)]

> [!NOTE]
> Domyślnie Windows Forms Designer przypisuje `private` (`Friend` w języku Visual Basic) modyfikatora kontenera formanty, takie jak <xref:System.Windows.Forms.Panel>. Jeśli podstawa <xref:System.Windows.Forms.UserControl> lub <xref:System.Windows.Forms.Form> zawiera formant kontenera nie będzie akceptować nowych elementów podrzędnych formularzy i kontrolek dziedziczone. Rozwiązaniem jest zmiana modyfikator kontrolki podstawowym kontenerem na `protected` lub `public`.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Button>
- [Formularze Windows Forms — dziedziczenie wizualizacji](windows-forms-visual-inheritance.md)
- [Przewodnik: Demonstrowanie dziedziczenia wizualizacji](walkthrough-demonstrating-visual-inheritance.md)
- [Instrukcje: Dziedziczenie formularzy Windows](how-to-inherit-windows-forms.md)
