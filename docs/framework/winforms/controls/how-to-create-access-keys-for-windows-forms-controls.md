---
title: 'Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy systemu Windows'
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
ms.openlocfilehash: ccec8bba9e01cbaa7bfef841af68a0fcaa720b90
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658379"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls"></a>Instrukcje: Tworzenie kluczy dostępu dla kontrolek Windows Forms

*Klucz dostępu* to podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak Button. Przy użyciu klucza dostępu użytkownik może "kliknąć" przycisk, naciskając klawisz Alt w połączeniu ze wstępnie zdefiniowanym kluczem dostępu. Na przykład, jeśli przycisk uruchamia procedurę w celu drukowania formularza, w związku z czym jej `Text` właściwość jest ustawiona na "Drukuj", dodając znak handlowego "i" "p" powoduje podkreślanie litery "p" w tekście przycisku w czasie wykonywania. Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze Alt + P.

Kontrolki, które nie mogą odbierać fokusu, nie mogą mieć kluczy dostępu.

## <a name="programmatic"></a>Program

`Text` Ustaw właściwość na ciąg, który zawiera znak handlowego "i" (&) przed literą, która będzie skrótem.

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
- [Instrukcje: Odpowiadanie na kliknięcia przycisku Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
