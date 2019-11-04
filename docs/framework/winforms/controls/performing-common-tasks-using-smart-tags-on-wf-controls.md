---
title: 'Wskazówki: przeprowadzanie typowych zadań z tagami inteligentnymi na formantach formularzy systemu Windows'
ms.date: 03/30/2017
helpviewer_keywords:
- DesignerAction object model
- smart tags
- designer actions
ms.assetid: cac337e6-00f6-4584-80f4-75728f5ea113
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 07fb43a711ae8b1e2e375b17b136c07f35b1cf39
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459575"
---
# <a name="walkthrough-perform-common-tasks-using-smart-tags"></a>Przewodnik: wykonywanie typowych zadań przy użyciu tagów inteligentnych

Podczas konstruowania formularzy i kontrolek dla aplikacji Windows Forms istnieje wiele zadań, które będą wykonywane wielokrotnie. Poniżej przedstawiono niektóre z najczęściej wykonywanych zadań:

- Dodawanie lub usuwanie karty na <xref:System.Windows.Forms.TabControl>.

- Dokowanie kontrolki do jej elementu nadrzędnego.

- Zmiana orientacji kontrolki <xref:System.Windows.Forms.SplitContainer>.

Aby przyspieszyć programowanie, wiele formantów oferuje Tagi inteligentne, które są menu kontekstowe, które umożliwiają wykonywanie typowych zadań, takich jak te w jednym gestie w czasie projektowania. Te zadania są nazywane *czasownikami tagów inteligentnych*.

Tagi inteligentne pozostają dołączone do wystąpienia kontroli dla jego okresu istnienia w Projektancie i są zawsze dostępne.

## <a name="create-the-project"></a>Utwórz projekt

Pierwszym krokiem jest utworzenie projektu i skonfigurowanie formularza.

1. W programie Visual Studio Utwórz projekt aplikacji oparty na systemie Windows o nazwie **SmartTagsExample**.

2. Wybierz formularz w **Projektant formularzy systemu Windows**.

## <a name="use-smart-tags"></a>Użyj tagów inteligentnych

Tagi inteligentne są zawsze dostępne w czasie projektowania na kontrolkach, które je oferują.

1. Przeciągnij <xref:System.Windows.Forms.TabControl> z **przybornika** do formularza. Zanotuj symbol inteligentny-tag (![symbol taga inteligentnego](./media/vs-winformsmttagglyph.gif)), który pojawia się po stronie <xref:System.Windows.Forms.TabControl>.

2. Kliknij symbol inteligentny-tag. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kartę** . Zwróć uwagę, że nowa strona karty zostanie dodana do <xref:System.Windows.Forms.TabControl>.

3. Przeciągnij kontrolkę <xref:System.Windows.Forms.TableLayoutPanel> z **przybornika** na formularz.

4. Kliknij symbol inteligentny-tag. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **Dodaj kolumnę** . Zwróć uwagę, że nowa kolumna jest dodawana do kontrolki <xref:System.Windows.Forms.TableLayoutPanel>.

5. Przeciągnij kontrolkę <xref:System.Windows.Forms.SplitContainer> z **przybornika** na formularz.

6. Kliknij symbol inteligentny-tag. W menu skrótów, które pojawia się obok glifu, wybierz pozycję **pozioma orientacja rozdzielacza** . Należy zauważyć, że pasek rozdzielacza kontrolki <xref:System.Windows.Forms.SplitContainer> jest teraz zorientowany w poziomie.

## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.TextBox>
- <xref:System.Windows.Forms.TabControl>
- <xref:System.Windows.Forms.SplitContainer>
- <xref:System.ComponentModel.Design.DesignerActionList>
