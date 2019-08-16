---
title: 'Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy systemu Windows przy użyciu narzędzia Projektant'
ms.date: 03/30/2017
helpviewer_keywords:
- controls [Windows Forms], access keys
- Button control [Windows Forms], access keys
- dialog box controls [Windows Forms], mnemonics
- access keys [Windows Forms], creating for controls
- mnemonics [Windows Forms], adding to dialog box controls
- ampersand character in shortcut key
- Windows Forms controls, access keys
- examples [Windows Forms], controls
- Text property [Windows Forms], specifying access keys for controls
- keyboard shortcuts [Windows Forms], creating for controls
- access keys [Windows Forms], Windows Forms
- ALT key
ms.assetid: 4c374c4c-4ca9-4a68-ac96-9dc3ab0f518a
ms.openlocfilehash: 01bed04483702ba2e62162b675aa1138bc1b0e01
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/15/2019
ms.locfileid: "69039521"
---
# <a name="how-to-create-access-keys-for-windows-forms-controls-using-the-designer"></a>Instrukcje: tworzenie klawiszy dostępu dla kontrolek formularzy systemu Windows przy użyciu narzędzia Projektant
*Klucz dostępu* to podkreślony znak w tekście menu, element menu lub etykieta kontrolki, takiej jak Button. Umożliwia użytkownikowi "klikanie" przycisku, naciskając klawisz ALT w połączeniu ze wstępnie zdefiniowanym kluczem dostępu. Na przykład, jeśli przycisk uruchamia procedurę do drukowania formularza, w związku z czym jej `Text` właściwość jest ustawiona na "Drukuj", dodając znak handlowego "i" (&) przed literą "p" powoduje podkreślanie litery "p" w tekście przycisku w czasie wykonywania. Użytkownik może uruchomić polecenie skojarzone z przyciskiem, naciskając klawisze ALT + P. Nie można mieć klucza dostępu dla kontrolki, która nie może odbierać fokusu.

## <a name="to-create-an-access-key-for-a-control"></a>Aby utworzyć klucz dostępu dla kontrolki

1. W oknie **Właściwości** Ustaw `Text` właściwość na ciąg, który zawiera znak handlowego "i" (&) przed literą, która będzie kluczem dostępu. Na przykład, aby ustawić literę "P" jako klucz dostępu, wpisz **& drukować** do siatki.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.Button>
- [Instrukcje: Odpowiadanie na kliknięcia przycisku Windows Forms](how-to-respond-to-windows-forms-button-clicks.md)
- [Instrukcje: Ustawianie tekstu wyświetlanego przez kontrolkę Windows Forms](how-to-set-the-text-displayed-by-a-windows-forms-control.md)
- [Etykietowanie pojedynczych kontrolek formularzy Windows Forms i określanie skrótów dla nich](labeling-individual-windows-forms-controls-and-providing-shortcuts-to-them.md)
