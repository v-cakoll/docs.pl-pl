---
title: Tworzenie kluczy dostępu dla kontrolek
ms.date: 08/20/2019
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- mnemonics
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4faa0991-28ec-4eca-91db-51dc2cd6a7ac
ms.openlocfilehash: 7f6b0a5838cacfc1189fba819a54b3423d567ea0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731171"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Instrukcje: tworzenie klawiszy dostępu dla kontrolek Windows Forms

*Klucz dostępu* to podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak Button. Przy użyciu klucza dostępu użytkownik może "kliknąć" przycisk, naciskając klawisz Alt w połączeniu ze wstępnie zdefiniowanym kluczem dostępu. Na przykład, jeśli przycisk uruchamia procedurę w celu wydrukowania formularza, a w związku z tym jej Właściwość `Text` jest ustawiona na "Drukuj", dodając znak handlowego "i" P "powoduje podkreślanie litery" P "w tekście przycisku w czasie wykonywania. Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze Alt + P.

Kontrolki, które nie mogą odbierać fokusu, nie mogą mieć kluczy dostępu.

## <a name="programmatic"></a>Programowa

Ustaw właściwość `Text` na ciąg, który zawiera znak handlowego "i" (&) przed literą, która będzie skrótem.

```vb
' Set the letter "P" as an access key.
Button1.Text = "&Print"
```

```csharp
// Set the letter "P" as an access key.
button1.Text = "&Print";
```

```cpp
// Set the letter "P" as an access key.
button1->Text = "&Print";
```

> [!NOTE]
> Aby użyć znaku handlowego "i" w podpisie bez tworzenia klucza dostępu, Uwzględnij dwa znaki handlowe (& &). W podpisie jest wyświetlany pojedynczy znak "i nie są podkreślane żadne znaki.

## <a name="designer"></a>Projektant

W oknie **Właściwości** programu Visual Studio ustaw właściwość **Text** na ciąg, który zawiera znak handlowego "i" ("&") przed literą, która będzie kluczem dostępu. Na przykład, aby ustawić literę "P" jako klucz dostępu, wprowadź **& Print**.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Button>
- [Instrukcje: odpowiadanie na kliknięcia przycisków Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
