---
title: Ustaw kolejność tabulacji kontrolek
description: Dowiedz się, jak ustawić kolejność tabulacji kontrolek na Windows Forms. Ustaw kolejność tabulacji przy użyciu programu Visual Studio lub Właściwość TabIndex w okno Właściwości.
ms.date: 03/30/2017
f1_keywords:
- TabStop
- TabIndex
helpviewer_keywords:
- tab order [Windows Forms], controls on Windows forms
- Windows Forms controls, setting tab order
- controls [Windows Forms], setting tab order
- Windows Forms, setting tab order
ms.assetid: 71fa8e76-0472-414b-ad3c-0f90166e0ad7
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 3d16da1ac73cc030b92bb36c4bfa3a79985339bf
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84903365"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Instrukcje: Ustawianie kolejności tabulacji na Windows Forms

Kolejność tabulacji to kolejność, w której użytkownik przenosi fokus z jednej kontrolki do innej przez wciśnięcie klawisza Tab. Każdy formularz ma własną kolejność tabulacji. Domyślnie kolejność tabulacji jest taka sama jak kolejność, w której zostały utworzone formanty. Numeracja kolejności tabulacji rozpoczyna się od zera.

## <a name="to-set-the-tab-order-of-a-control"></a>Aby ustawić kolejność tabulacji kontrolki

1. W programie Visual Studio, w menu **Widok** wybierz **kolejność tabulacji**.

   Aktywuje to tryb wyboru kolejności tabulacji w formularzu. Liczba (reprezentująca <xref:System.Windows.Forms.Control.TabIndex%2A> Właściwość) pojawia się w lewym górnym rogu każdej kontrolki.

2. Klikaj kontrolki sekwencyjnie, aby ustalić kolejność tabulacji.

   > [!NOTE]
   > Dla kontrolki w kolejności tabulacji można ustawić dowolną wartość większą lub równą 0. W przypadku występowania duplikatów porządek osi z dwóch kontrolek jest oceniany, a kontrolka na górze jest z tabulacją na pierwszy. (Kolejność z jest wizualną warstwą formantów w formularzu wzdłuż osi z [głębokość]). Porządek osi z określa, które kontrolki znajdują się przed innymi kontrolkami. Aby uzyskać więcej informacji na temat porządku osi z, zobacz [warstwowanie obiektów na Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Po zakończeniu wybierz pozycję **kolejność tabulacji** w menu **Widok** , aby pozostawić tryb kolejności tabulacji.

   > [!NOTE]
   > Kontrolki, które nie mogą uzyskać fokusu, a także wyłączone i niewidoczne kontrolki, nie mają <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości i nie są uwzględnione w kolejności tabulacji. Gdy użytkownik naciśnie klawisz Tab, te kontrolki są pomijane.

Alternatywnie można ustawić kolejność tabulacji w okno Właściwości przy użyciu <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości. <xref:System.Windows.Forms.Control.TabIndex%2A>Właściwość kontrolki określa miejsce, w którym jest umieszczony w kolejności tabulacji. Domyślnie pierwszy rysowany formant ma <xref:System.Windows.Forms.Control.TabIndex%2A> wartość 0, a druga — <xref:System.Windows.Forms.Control.TabIndex%2A> od 1 itd.

Ponadto domyślnie <xref:System.Windows.Forms.GroupBox> kontrolka ma własną <xref:System.Windows.Forms.Control.TabIndex%2A> wartość, która jest liczbą całkowitą. <xref:System.Windows.Forms.GroupBox>Kontrolka nie może mieć fokusu w czasie wykonywania. W tym celu każda kontrolka w ramach <xref:System.Windows.Forms.GroupBox> ma własną <xref:System.Windows.Forms.Control.TabIndex%2A> wartość dziesiętną, zaczynając od. 0. W naturalny sposób, gdy <xref:System.Windows.Forms.Control.TabIndex%2A> <xref:System.Windows.Forms.GroupBox> kontrolka jest zwiększana, zostaną odpowiednio zwiększone. Jeśli zmieniono <xref:System.Windows.Forms.Control.TabIndex%2A> wartość z przedziału od 5 do 6, <xref:System.Windows.Forms.Control.TabIndex%2A> wartość pierwszej kontrolki w grupie automatycznie zmieni się na 6,0 itd.

Na koniec w kolejności tabulacji można pominąć dowolną kontrolkę wiele w formularzu. Zwykle naciśnięcie klawisza Tab w czasie wykonywania wybiera każdy formant w kolejności tabulacji. Wyłączenie <xref:System.Windows.Forms.Control.TabStop%2A> Właściwości umożliwia przekazanie kontrolki w kolejności tabulacji w formularzu.

## <a name="to-remove-a-control-from-the-tab-order"></a>Aby usunąć formant z kolejności tabulacji

Ustaw właściwość kontrolki <xref:System.Windows.Forms.Control.TabStop%2A> na **false** w oknie **Właściwości** .

Formant, którego <xref:System.Windows.Forms.Control.TabStop%2A> Właściwość została ustawiona tak, aby `false` nadal utrzymuje swoją pozycję w kolejności tabulacji, nawet jeśli formant zostanie pominięty podczas przechodzenia przez kontrolki za pomocą klawisza Tab.

> [!NOTE]
> Grupa przycisków radiowych ma jeden tabulator w czasie wykonywania. Wybrany przycisk (czyli przycisk z <xref:System.Windows.Forms.RadioButton.Checked%2A> właściwością ustawioną na `true` ) ma <xref:System.Windows.Forms.Control.TabStop%2A> ustawioną właściwość automatycznie na `true` , a pozostałe przyciski mają <xref:System.Windows.Forms.Control.TabStop%2A> ustawioną właściwość `false` . Aby uzyskać więcej informacji na temat <xref:System.Windows.Forms.RadioButton> formantów grupowania, zobacz [grupowanie Windows Forms formantów RadioButton do działania jako zestaw](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Zobacz też

- [Kontrolki Windows Forms](index.md)
- [Formanty do użycia w formularzach systemu Windows](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
