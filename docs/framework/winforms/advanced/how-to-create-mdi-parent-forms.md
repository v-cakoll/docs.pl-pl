---
title: 'Porady: tworzenie formularzy nadrzędnych MDI'
description: Dowiedz się, jak utworzyć formularz nadrzędny MDI programowo i przy użyciu Projektant formularzy systemu Windows.
ms.date: 03/30/2017
helpviewer_keywords:
- parent forms
- MDI [Windows Forms], creating forms
ms.assetid: 12c71221-2377-4bb6-b10b-7b4b300fd462
ms.openlocfilehash: d387837a565ca247f62828c19f353990b35117c7
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174708"
---
# <a name="how-to-create-mdi-parent-forms"></a>Porady: tworzenie formularzy nadrzędnych MDI

> [!IMPORTANT]
> W tym temacie jest używany <xref:System.Windows.Forms.MainMenu> formant, który został zastąpiony przez <xref:System.Windows.Forms.MenuStrip> formant. W <xref:System.Windows.Forms.MainMenu> przypadku wybrania tej opcji formant jest zachowywany zarówno w przypadku zgodności z poprzednimi wersjami, jak i w przyszłości. Aby uzyskać informacje na temat tworzenia formularza nadrzędnego MDI przy użyciu <xref:System.Windows.Forms.MenuStrip> , zobacz [How to: Create a MDI Window list with MenuStrip](../controls/how-to-create-an-mdi-window-list-with-menustrip-windows-forms.md).

Podstawą aplikacji interfejsu wielu dokumentów (MDI) jest formularz nadrzędny MDI. Jest to formularz zawierający okna podrzędne MDI, które są podsystemem Windows, w którym użytkownik współdziała z aplikacją MDI. Tworzenie formularza nadrzędnego MDI jest proste, zarówno w Projektant formularzy systemu Windows, jak i programowo.

## <a name="create-an-mdi-parent-form-at-design-time"></a>Utwórz formularz nadrzędny MDI w czasie projektowania

1. Utwórz projekt aplikacji systemu Windows w programie Visual Studio.

2. W oknie **Właściwości** Ustaw <xref:System.Windows.Forms.Form.IsMdiContainer%2A> Właściwość na **wartość true**.

     Oznacza to, że formularz jest kontenerem MDI dla okien podrzędnych.

    > [!NOTE]
    > Podczas ustawiania właściwości w oknie **Właściwości** , można również ustawić `WindowState` Właściwość na **zmaksymalizowane**, jeśli chcesz, ponieważ jest to najłatwiej manipulować oknami podrzędnymi MDI po zmaksymalizowaniu formularza nadrzędnego. Ponadto należy pamiętać, że krawędź formularza nadrzędnego MDI spowoduje pobranie koloru systemu (ustawianego w panelu sterowania systemu Windows), a nie koloru tyłu ustawianego przy użyciu <xref:System.Windows.Forms.Control.BackColor%2A?displayProperty=nameWithType> właściwości.

3. Z **przybornika**przeciągnij formant **MenuStrip** do formularza. Utwórz element menu najwyższego poziomu z właściwością **Text** ustawioną na **&pliku** z elementami podmenu o nazwie **&New** i **&Close**. Utwórz także element menu najwyższego poziomu o nazwie **&okno**.

     Pierwsze menu spowoduje utworzenie i ukrycie elementów menu w czasie wykonywania, a drugie menu będzie śledzić otwarte okna podrzędne MDI. W tym momencie utworzono okno nadrzędne MDI.

4. Naciśnij klawisz **F5** , aby uruchomić aplikację. Aby uzyskać informacje na temat tworzenia okien podrzędnych MDI, które działają w ramach formularza nadrzędnego MDI, zobacz [How to: Create MDI Child Forms](how-to-create-mdi-child-forms.md).

## <a name="see-also"></a>Zobacz też

- [Aplikacje interfejsu wielu dokumentów (MDI)](multiple-document-interface-mdi-applications.md)
- [Porady: tworzenie formularzy podrzędnych MDI](how-to-create-mdi-child-forms.md)
- [Instrukcje: określanie elementu podrzędnego MDI Active](how-to-determine-the-active-mdi-child.md)
- [Instrukcje: wysyłanie danych do Active MDI Child](how-to-send-data-to-the-active-mdi-child.md)
- [Porady: aranżowanie formularzy podrzędnych MDI](how-to-arrange-mdi-child-forms.md)
