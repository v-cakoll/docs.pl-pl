---
title: Wykonywanie typowych zadań przy użyciu akcji projektanta na kontrolkach
ms.date: 02/13/2019
helpviewer_keywords:
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 342741b9ce032b1b8ec50a6c689d9109d12f5b3b
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77634884"
---
# <a name="walkthrough-perform-common-tasks-using-designer-actions"></a>Przewodnik: wykonywanie typowych zadań przy użyciu akcji projektanta

Podczas konstruowania formularzy i kontrolek dla aplikacji Windows Forms istnieje wiele zadań, które będą wykonywane wielokrotnie. Na poniższej liście przedstawiono niektóre z najczęściej wykonywanych zadań:

- Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.
- Dokowanie kontrolki do jej elementu nadrzędnego.
- Zmiana orientacji kontrolki <xref:System.Windows.Forms.SplitContainer>.

Aby przyspieszyć programowanie, wiele formantów oferuje akcje projektanta, które są kontekstowymi menu, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestie w czasie projektowania. Te zadania są nazywane *zleceniami akcji projektanta*.

Akcje projektanta pozostają dołączone do wystąpienia kontroli dla jego okresu istnienia w Projektancie i są zawsze dostępne.

## <a name="create-the-project"></a>Tworzenie projektu

Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.

1. W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie **DesignerActionsExample**.

2. Wybierz formularz w **Projektant formularzy systemu Windows**.

## <a name="use-designer-actions"></a>Korzystanie z akcji projektanta

Akcje projektanta są zawsze dostępne w czasie projektowania na kontrolkach, które je oferują.

1. Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** do formularza. Zwróć uwagę na to, że glif akcji projektanta (![małą czarną strzałką](./media/designer-actions-glyph.gif)) pojawia się po stronie <xref:System.Windows.Forms.TabControl>.

2. Kliknij symbol akcji projektanta. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kartę** . Zwróć uwagę, że nowa strona karty zostanie dodana do <xref:System.Windows.Forms.TabControl>.

3. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.

4. Kliknij symbol akcji projektanta. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kolumnę** . Zwróć uwagę, że nowa kolumna jest dodawana do kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.

5. Przeciągnij kontrolkę <xref:System.Windows.Forms.SplitContainer> z **przybornika** na formularz.

6. Kliknij symbol akcji projektanta. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **pozioma orientacja rozdzielacza** . Należy zauważyć, że pasek rozdzielacza kontrolki <xref:System.Windows.Forms.SplitContainer> jest teraz zorientowany w poziomie.

## <a name="see-also"></a>Zobacz też

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
