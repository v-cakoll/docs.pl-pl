---
title: 'Porady: ustawianie kolejności tabulacji na formularzach systemu Windows'
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
ms.openlocfilehash: 026cff06a8d662cb40107fa76cf6d7989fe30cf1
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458524"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Instrukcje: Ustawianie kolejności tabulacji na Windows Forms

Kolejność tabulacji to kolejność, w której użytkownik przenosi fokus z jednej kontrolki do innej przez wciśnięcie klawisza Tab. Każdy formularz ma własną kolejność tabulacji. Domyślnie kolejność tabulacji jest taka sama jak kolejność, w której zostały utworzone formanty. Numeracja kolejności tabulacji rozpoczyna się od zera.

## <a name="to-set-the-tab-order-of-a-control"></a>Aby ustawić kolejność tabulacji kontrolki

1. W programie Visual Studio, w menu **Widok** wybierz **kolejność tabulacji**.

   Aktywuje to tryb wyboru kolejności tabulacji w formularzu. Liczba (reprezentująca Właściwość <xref:System.Windows.Forms.Control.TabIndex%2A>) pojawia się w lewym górnym rogu każdej kontrolki.

2. Klikaj kontrolki sekwencyjnie, aby ustalić kolejność tabulacji.

   > [!NOTE]
   > Dla kontrolki w kolejności tabulacji można ustawić dowolną wartość większą lub równą 0. W przypadku występowania duplikatów porządek osi z dwóch kontrolek jest oceniany, a kontrolka na górze jest z tabulacją na pierwszy. (Kolejność z jest wizualną warstwą formantów w formularzu wzdłuż osi z [głębokość]). Porządek osi z określa, które kontrolki znajdują się przed innymi kontrolkami. Aby uzyskać więcej informacji na temat porządku osi z, zobacz [warstwowanie obiektów na Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Po zakończeniu wybierz pozycję **kolejność tabulacji** w menu **Widok** , aby pozostawić tryb kolejności tabulacji.

   > [!NOTE]
   > Kontrolki, które nie mogą uzyskać fokusu, a także wyłączone i niewidoczne kontrolki, nie mają właściwości <xref:System.Windows.Forms.Control.TabIndex%2A> i nie są uwzględnione w kolejności tabulacji. Gdy użytkownik naciśnie klawisz Tab, te kontrolki są pomijane.

Alternatywnie można ustawić kolejność tabulacji w okno Właściwości przy użyciu właściwości <xref:System.Windows.Forms.Control.TabIndex%2A>. Właściwość <xref:System.Windows.Forms.Control.TabIndex%2A> formantu określa miejsce, w którym jest umieszczane w kolejności tabulacji. Domyślnie pierwszy rysowany formant ma <xref:System.Windows.Forms.Control.TabIndex%2A> wartość 0, a drugi ma <xref:System.Windows.Forms.Control.TabIndex%2A> 1 itd.

Ponadto domyślnie formant <xref:System.Windows.Forms.GroupBox> ma własną wartość <xref:System.Windows.Forms.Control.TabIndex%2A>, która jest liczbą całkowitą. Sama kontrolka <xref:System.Windows.Forms.GroupBox> nie może mieć fokusu w czasie wykonywania. W tym celu każda kontrolka w <xref:System.Windows.Forms.GroupBox> ma własną wartość dziesiętną <xref:System.Windows.Forms.Control.TabIndex%2A>, zaczynając od. 0. Naturalnie, ponieważ <xref:System.Windows.Forms.Control.TabIndex%2A> kontrolki <xref:System.Windows.Forms.GroupBox> jest zwiększane, zostaną odpowiednio narastane. Jeśli zmieniono wartość <xref:System.Windows.Forms.Control.TabIndex%2A> z przedziału od 5 do 6, wartość <xref:System.Windows.Forms.Control.TabIndex%2A> pierwszej kontrolce w swojej grupie automatycznie zmieni się na 6,0 itd.

Na koniec w kolejności tabulacji można pominąć dowolną kontrolkę wiele w formularzu. Zwykle naciśnięcie klawisza Tab w czasie wykonywania wybiera każdy formant w kolejności tabulacji. Wyłączenie właściwości <xref:System.Windows.Forms.Control.TabStop%2A> umożliwia przekazanie kontrolki w kolejności tabulacji w formularzu.

## <a name="to-remove-a-control-from-the-tab-order"></a>Aby usunąć formant z kolejności tabulacji

Ustaw właściwość <xref:System.Windows.Forms.Control.TabStop%2A> kontrolki na **wartość false** w oknie **Właściwości** .

Kontrolka, której Właściwość <xref:System.Windows.Forms.Control.TabStop%2A> została ustawiona na `false` nadal utrzymuje swoją pozycję w kolejności tabulacji, nawet jeśli formant zostanie pominięty podczas przechodzenia przez kontrolki za pomocą klawisza Tab.

> [!NOTE]
> Grupa przycisków radiowych ma jeden tabulator w czasie wykonywania. Wybrany przycisk (czyli przycisk z właściwością <xref:System.Windows.Forms.RadioButton.Checked%2A> ustawioną na `true`) ma właściwość <xref:System.Windows.Forms.Control.TabStop%2A> automatycznie ustawiona na `true`, podczas gdy inne przyciski mają swoją właściwość <xref:System.Windows.Forms.Control.TabStop%2A> ustawioną na `false`. Aby uzyskać więcej informacji na temat grupowania formantów <xref:System.Windows.Forms.RadioButton>, zobacz [grupowanie Windows Forms formantów RadioButton do działania jako zestaw](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
