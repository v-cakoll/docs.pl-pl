---
title: 'Porady: tworzenie warstw obiektów na formularzach systemu Windows'
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
ms.openlocfilehash: 5b8f6c00e70df94ae3a82c2c195fa781f0840a53
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458356"
---
# <a name="how-to-layer-objects-on-windows-forms"></a>Instrukcje: obiekty warstwy na Windows Forms

Podczas tworzenia złożonego interfejsu użytkownika lub pracy z formularzem interfejsu wielu dokumentów (MDI), często zajdzie potrzeba warstwy formantów i formularzy podrzędnych, aby utworzyć bardziej złożone interfejsy użytkownika. Aby przenieść i śledzić kontrolki i okna w kontekście grupy, można manipulować ich *kolejnością z*. Porządek osi z jest wizualną warstwą formantów w formularzu wzdłuż osi z (głębokości) formularza. Okno w górnej części porządku osi z nakładają się na wszystkie inne okna. Wszystkie inne okna nakładają się na okno w dolnej części porządku osi z.

## <a name="to-layer-controls-at-design-time"></a>Do kontrolek warstwy w czasie projektowania

1. W programie Visual Studio Wybierz kontrolkę, którą chcesz przydzielyć do warstwy.

2. W menu **Format** wybierz pozycję **Zamówienie**, a następnie wybierz pozycję **Przesuń na wierzch** lub **Przesuń na spód**.

## <a name="to-layer-controls-programmatically"></a>Na programistyczne kontrolki warstwy

Użyj metod <xref:System.Windows.Forms.Control.BringToFront%2A> i <xref:System.Windows.Forms.Control.SendToBack%2A> do manipulowania kolejnością z kontrolek z.

Na przykład, jeśli formant <xref:System.Windows.Forms.TextBox>, `txtFirstName`, znajduje się pod inną kontrolką i chcesz go umieścić na górze, użyj następującego kodu:

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
> Windows Forms obsługuje *zawieranie kontrolek*. Zawieranie kontrolek obejmuje umieszczenie wielu kontrolek w obrębie zawierającej kontrolki, takich jak liczba formantów <xref:System.Windows.Forms.RadioButton> w kontrolce <xref:System.Windows.Forms.GroupBox>. Następnie można przyciągać warstwy do kontrolek zawierających. Przeniesienie pola grupy przenosi również kontrolki, ponieważ znajdują się w nim.

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
