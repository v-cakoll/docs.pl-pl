---
title: Obiekty układu
description: Dowiedz się, jak tworzyć warstwy obiektów w kontrolkach Windows Forms i formularzach podrzędnych w celu tworzenia bardziej złożonych interfejsów użytkownika.
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
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 6269b09c56963fefd500b9e1e6c9d7f51f9619cf
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174513"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Instrukcje: obiekty warstwy na Windows Forms

Podczas tworzenia złożonego interfejsu użytkownika lub pracy z formularzem interfejsu wielu dokumentów (MDI), często zajdzie potrzeba warstwy formantów i formularzy podrzędnych, aby utworzyć bardziej złożone interfejsy użytkownika. Aby przenieść i śledzić kontrolki i okna w kontekście grupy, można manipulować ich *kolejnością z*. Porządek osi z jest wizualną warstwą formantów w formularzu wzdłuż osi z (głębokości) formularza. Okno w górnej części porządku osi z nakładają się na wszystkie inne okna. Wszystkie inne okna nakładają się na okno w dolnej części porządku osi z.

## <a name="to-layer-controls-at-design-time"></a>Do kontrolek warstwy w czasie projektowania

1. W programie Visual Studio Wybierz kontrolkę, którą chcesz przydzielyć do warstwy.

2. W menu **Format** wybierz pozycję **Zamówienie**, a następnie wybierz pozycję **Przesuń na wierzch** lub **Przesuń na spód**.

## <a name="to-layer-controls-programmatically"></a>Na programistyczne kontrolki warstwy

Użyj <xref:System.Windows.Forms.Control.BringToFront%2A> metod i, <xref:System.Windows.Forms.Control.SendToBack%2A> aby manipulować kolejnością z w formantach z.

Na przykład, jeśli <xref:System.Windows.Forms.TextBox> formant, `txtFirstName` znajduje się pod inną kontrolką i chcesz go umieścić na górze, użyj następującego kodu:

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
> Windows Forms obsługuje *zawieranie kontrolek*. Zawieranie formantów obejmuje umieszczanie wielu kontrolek w obrębie zawierającej kontrolki, takich jak liczba <xref:System.Windows.Forms.RadioButton> kontrolek w <xref:System.Windows.Forms.GroupBox> kontrolce. Następnie można przyciągać warstwy do kontrolek zawierających. Przeniesienie pola grupy przenosi również kontrolki, ponieważ znajdują się w nim.

## <a name="see-also"></a>Zobacz też

- [Kontrolki Windows Forms](index.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
