---
title: 'Instrukcje: ustawianie kolejności tabulacji na formularzach systemu Windows'
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
ms.openlocfilehash: 0a6cd8b16148d28049549b241b568966239b9b01
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923613"
---
# <a name="how-to-set-the-tab-order-on-windows-forms"></a>Instrukcje: ustawianie kolejności tabulacji na formularzach systemu Windows
Kolejność tabulacji to kolejność, w której użytkownik przenosi fokus z jednej kontrolki do innej przez wciśnięcie klawisza TAB. Każdy formularz ma własną kolejność tabulacji. Domyślnie kolejność tabulacji jest taka sama jak kolejność, w której zostały utworzone formanty. Numeracja kolejności tabulacji rozpoczyna się od zera.

## <a name="to-set-the-tab-order-of-a-control"></a>Aby ustawić kolejność tabulacji kontrolki

1. W menu **Widok** kliknij **kolejność tabulacji**.

     Aktywuje to tryb wyboru kolejności tabulacji w formularzu. Liczba (reprezentująca <xref:System.Windows.Forms.Control.TabIndex%2A> Właściwość) pojawia się w lewym górnym rogu każdej kontrolki.

2. Klikaj kontrolki sekwencyjnie, aby ustalić kolejność tabulacji.

    > [!NOTE]
    > Dla kontrolki w kolejności tabulacji można ustawić dowolną wartość większą lub równą 0. W przypadku występowania duplikatów porządek osi z dwóch kontrolek jest oceniany, a kontrolka na górze jest z tabulacją na pierwszy. (Kolejność z jest wizualną warstwą formantów w formularzu wzdłuż osi z [głębokość]). Porządek osi z określa, które kontrolki znajdują się przed innymi kontrolkami. Aby uzyskać więcej informacji na temat porządku osi z, zobacz [warstwowanie obiektów na Windows Forms](how-to-layer-objects-on-windows-forms.md).

3. Po zakończeniu kliknij pozycję **kolejność tabulacji** w menu **Widok** , aby pozostawić tryb kolejności tabulacji.

    > [!NOTE]
    > Kontrolki, które nie mogą uzyskać fokusu, a także wyłączone i niewidoczne kontrolki, <xref:System.Windows.Forms.Control.TabIndex%2A> nie mają właściwości i nie są uwzględnione w kolejności tabulacji. Gdy użytkownik naciśnie klawisz TAB, te kontrolki są pomijane.

 Alternatywnie można ustawić kolejność tabulacji w okno właściwości przy użyciu <xref:System.Windows.Forms.Control.TabIndex%2A> właściwości. <xref:System.Windows.Forms.Control.TabIndex%2A> Właściwość kontrolki określa miejsce, w którym jest umieszczony w kolejności tabulacji. Domyślnie pierwszy rysowany formant ma <xref:System.Windows.Forms.Control.TabIndex%2A> wartość 0, a druga <xref:System.Windows.Forms.Control.TabIndex%2A> — od 1 itd.

 Ponadto domyślnie <xref:System.Windows.Forms.GroupBox> kontrolka ma własną <xref:System.Windows.Forms.Control.TabIndex%2A> wartość, która jest liczbą całkowitą. <xref:System.Windows.Forms.GroupBox> Kontrolka nie może mieć fokusu w czasie wykonywania. W tym celu każda kontrolka <xref:System.Windows.Forms.GroupBox> w ramach ma własną <xref:System.Windows.Forms.Control.TabIndex%2A> wartość dziesiętną, zaczynając od. 0. W naturalny sposób, <xref:System.Windows.Forms.Control.TabIndex%2A> gdy <xref:System.Windows.Forms.GroupBox> kontrolka jest zwiększana, zostaną odpowiednio zwiększone. Jeśli zmieniono <xref:System.Windows.Forms.Control.TabIndex%2A> wartość z przedziału od 5 do 6 <xref:System.Windows.Forms.Control.TabIndex%2A> , wartość pierwszej kontrolki w grupie automatycznie zmieni się na 6,0 itd.

 Na koniec w kolejności tabulacji można pominąć dowolną kontrolkę wiele w formularzu. Zwykle naciśnięcie klawisza TAB w czasie wykonywania wybiera każdy formant w kolejności tabulacji. Wyłączenie <xref:System.Windows.Forms.Control.TabStop%2A> właściwości umożliwia przekazanie kontrolki w kolejności tabulacji w formularzu.

## <a name="to-remove-a-control-from-the-tab-order"></a>Aby usunąć formant z kolejności tabulacji

1. Ustaw <xref:System.Windows.Forms.Control.TabStop%2A> właściwość kontrolki na `false` okno właściwości.

     Formant, którego <xref:System.Windows.Forms.Control.TabStop%2A> właściwość została ustawiona tak, `false` aby nadal utrzymuje swoją pozycję w kolejności tabulacji, nawet jeśli formant zostanie pominięty podczas przechodzenia przez kontrolki za pomocą klawisza Tab.

    > [!NOTE]
    > Grupa przycisków radiowych ma jeden tabulator w czasie wykonywania. Wybrany przycisk (czyli <xref:System.Windows.Forms.RadioButton.Checked%2A> przycisk z właściwością ustawioną na `true`) ma <xref:System.Windows.Forms.Control.TabStop%2A> ustawioną właściwość automatycznie <xref:System.Windows.Forms.Control.TabStop%2A> na `true`, a pozostałe przyciski mają ustawioną `false`właściwość. Aby uzyskać więcej informacji na <xref:System.Windows.Forms.RadioButton> temat formantów grupowania, zobacz [grupowanie Windows Forms formantów RadioButton do działania jako zestaw](how-to-group-windows-forms-radiobutton-controls-to-function-as-a-set.md).

## <a name="see-also"></a>Zobacz także

- [Kontrolki formularzy Windows Forms](index.md)
- [Rozmieszczanie kontrolek na formularzach Windows Forms](arranging-controls-on-windows-forms.md)
- [Kontrolki do użycia w formularzach Windows Forms](controls-to-use-on-windows-forms.md)
- [Kontrolki formularzy Windows Forms według funkcji](windows-forms-controls-by-function.md)
