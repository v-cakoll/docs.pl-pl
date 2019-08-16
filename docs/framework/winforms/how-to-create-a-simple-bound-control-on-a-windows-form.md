---
title: 'Instrukcje: Tworzenie prostej kontrolki powiązanej na formularzu Windows Form'
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], simple data binding
- Windows Forms controls, data binding
ms.assetid: 3bcaded8-0f1a-4cc0-8830-f59be253bf4e
ms.openlocfilehash: ed1d0e423a3cdf77a242ec3214720f1466f65897
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039506"
---
# <a name="how-to-create-a-simple-bound-control-on-a-windows-form"></a>Instrukcje: Tworzenie prostej kontrolki powiązanej na formularzu Windows Form

Przy użyciu *prostego powiązania*można wyświetlić pojedynczy element danych, taki jak wartość kolumny z tabeli zestawu danych, w formancie. Można utworzyć prostą dowolną właściwość formantu do wartości danych.

### <a name="to-simple-bind-a-control"></a>Aby powiązać formant z prostą

1. Nawiąż połączenie ze źródłem danych. Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).

2. W formularzu zaznacz kontrolkę i Wyświetl okno **Właściwości** .

3. Rozwiń Właściwość **(DataBindings)** .

     Właściwości najczęściej powiązane są wyświetlane pod właściwością **(DataBindings)** . Na przykład w większości formantów właściwość **Text** jest najczęściej powiązana.

4. Jeśli właściwość, którą chcesz powiązać, nie jest jedną z często powiązanych właściwości, kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości ](./media/how-to-create-a-simple-bound-control-on-a-windows-form/visual-studio-ellipsis-button.png)programu Visual Studio) w polu **(Zaawansowane)** , aby wyświetlić  **Formatowanie i zaawansowane** okno dialogowe powiązania z pełną listą właściwości tej kontrolki.

5. Wybierz właściwość, którą chcesz powiązać, a następnie kliknij strzałkę listy rozwijanej w obszarze **powiązania**.

     Zostanie wyświetlona lista dostępnych źródeł danych.

6. Rozwiń źródło danych, do którego chcesz powiązać, dopóki nie znajdziesz jednego z nich. Na przykład jeśli powiążesz się z wartością kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.

7. Kliknij nazwę elementu, z którym ma zostać utworzone powiązanie.

8. Jeśli pracujesz w oknie dialogowym **Formatowanie i zaawansowane powiązanie** , kliknij przycisk **OK** , aby powrócić do okna **Właściwości** .

9. Jeśli chcesz powiązać dodatkowe właściwości kontrolki, powtórz kroki od 3 do 7.

    > [!NOTE]
    > Ponieważ kontrolki proste powiązane pokazują tylko jeden element danych, jest to bardzo typowy do uwzględnienia logiki nawigacji w formularzu systemu Windows z prostymi kontrolkami.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Binding>
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
