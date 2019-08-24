---
title: 'Przewodnik: przeprowadzanie typowych zadań z tagami inteligentnymi na kontrolkach formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 34c14c0afd9632b06947fd72e46ddbda070cfb0f
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015766"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Przewodnik: Wykonywanie typowych zadań przy użyciu tagów inteligentnych

Podczas konstruowania formularzy i kontrolek dla aplikacji Windows Forms istnieje wiele zadań, które będą wykonywane wielokrotnie. Poniżej przedstawiono niektóre z najczęściej wykonywanych zadań:

- Dodawanie lub usuwanie karty w <xref:System.Windows.Forms.TabControl>.

- Dokowanie kontrolki do jej elementu nadrzędnego.

- Zmiana orientacji <xref:System.Windows.Forms.SplitContainer> formantu.

Aby przyspieszyć programowanie, wiele formantów oferuje Tagi inteligentne, które są menu kontekstowe, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestie w czasie projektowania. Te zadania są nazywane *czasownikami tagów inteligentnych*.

Tagi inteligentne pozostają dołączone do wystąpienia kontroli dla jego okresu istnienia w Projektancie i są zawsze dostępne.

## <a name="create-the-project"></a>Utwórz projekt

Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.

1. W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie **SmartTagsExample**.

2. Wybierz formularz w **Projektant formularzy systemu Windows**.

## <a name="use-smart-tags"></a>Użyj tagów inteligentnych

Tagi inteligentne są zawsze dostępne w czasie projektowania na kontrolkach, które je oferują.

1. Przeciągnij z <xref:System.Windows.Forms.TabControl> przybornika do formularza. Zanotuj symbol inteligentny (![symbol](./media/vs-winformsmttagglyph.gif)tagu inteligentnego), który pojawia się po stronie <xref:System.Windows.Forms.TabControl>.

2. Kliknij symbol inteligentny-tag. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kartę** . Zwróć uwagę, że nowa strona karty jest dodawana <xref:System.Windows.Forms.TabControl>do.

3. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.TableLayoutPanel>

4. Kliknij symbol inteligentny-tag. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kolumnę** . Zwróć uwagę, że nowa kolumna jest dodawana <xref:System.Windows.Forms.TableLayoutPanel> do kontrolki.

5. Przeciągnij kontrolkę z przybornika do formularza. <xref:System.Windows.Forms.SplitContainer>

6. Kliknij symbol inteligentny-tag. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **pozioma orientacja rozdzielacza** . Należy zauważyć, <xref:System.Windows.Forms.SplitContainer> że pasek rozdzielacza kontrolki jest teraz zorientowany w poziomie.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
