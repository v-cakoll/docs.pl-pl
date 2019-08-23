---
title: 'Instrukcje: tworzenie warstw obiektów na formularzach systemu Windows'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- Windows Forms controls, layering
- controls [Windows Forms], layering
- z order
- controls [Windows Forms], positioning
- z-order
ms.assetid: 1acc4281-2976-4715-86f4-bda68134baaf
ms.openlocfilehash: 818f36633575b248d92da475c462cc0f211fe969
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966538"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Instrukcje: tworzenie warstw obiektów na formularzach systemu Windows
Podczas tworzenia złożonego interfejsu użytkownika lub pracy z formularzem interfejsu wielu dokumentów (MDI), często zajdzie potrzeba warstwy formantów i formularzy podrzędnych, aby utworzyć bardziej złożone interfejsy użytkownika. Aby przenieść i śledzić kontrolki i okna w kontekście grupy, można manipulować ich kolejnością z. *Porządek osi z* jest wizualną warstwą formantów w formularzu wzdłuż osi z (głębokości) formularza. Okno w górnej części porządku osi z nakładają się na wszystkie inne okna. Wszystkie inne okna nakładają się na okno w dolnej części porządku osi z.

## <a name="to-layer-controls-at-design-time"></a>Do kontrolek warstwy w czasie projektowania

1. Wybierz kontrolkę, którą chcesz przydzielyć do warstwy.

2. W menu **Format** wskaż polecenie **kolejność**, a następnie kliknij pozycję **Przesuń na wierzch** lub **Przesuń na spód**.

## <a name="to-layer-controls-programmatically"></a>Na programistyczne kontrolki warstwy

- Użyj metod <xref:System.Windows.Forms.Control.SendToBack%2A> i, aby manipulować kolejnością z w formantach z. <xref:System.Windows.Forms.Control.BringToFront%2A>

     Na przykład, jeśli <xref:System.Windows.Forms.TextBox> formant, `txtFirstName`znajduje się pod inną kontrolką i chcesz go umieścić na górze, użyj następującego kodu:

    ```vb
    txtFirstName.BringToFront()
    ```

    ```csharp
    txtFirstName.BringToFront();
    ```

    ```cpp
    txtFirstName->BringToFront();
    ```

> [!NOTE]
> Windows Forms obsługuje *zawieranie kontrolek*. Zawieranie formantów obejmuje umieszczanie wielu kontrolek w obrębie zawierającej kontrolki, takich jak liczba <xref:System.Windows.Forms.RadioButton> kontrolek <xref:System.Windows.Forms.GroupBox> w kontrolce. Następnie można przyciągać warstwy do kontrolek zawierających. Przeniesienie pola grupy przenosi również kontrolki, ponieważ znajdują się w nim.

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
