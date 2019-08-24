---
title: 'Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 543775894994c518d6069f697b145cedaa7af5b0
ms.sourcegitcommit: 121ab70c1ebedba41d276e436dd2b1502748a49f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/24/2019
ms.locfileid: "70015661"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych

Za pomocą powiązania danych Windows Forms można sformatować dane wyświetlane w kontrolce powiązanej z danymi przy użyciu okna dialogowego **Formatowanie i powiązanie zaawansowane** .

## <a name="to-bind-a-control-and-format-the-displayed-data"></a>Aby powiązać formant i sformatować wyświetlane dane

1. Nawiąż połączenie ze źródłem danych. Aby uzyskać więcej informacji, zobacz [nawiązywanie połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).

2. W programie Visual Studio zaznacz kontrolkę w formularzu, a następnie otwórz okno **Właściwości** .

3. Rozwiń Właściwość **(DataBindings)** , a następnie w polu **(Zaawansowane)** kliknij przycisk wielokropka (![przycisk wielokropka (...) w okno właściwości programu Visual Studio](./media/how-to-create-a-bound-control-and-format-the-displayed-data/visual-studio-ellipsis-button.png)), aby wyświetlić **Formatowanie i zaawansowane** Okno dialogowe powiązania, które zawiera kompletną listę właściwości tej kontrolki.

4. Wybierz właściwość, którą chcesz powiązać, a następnie wybierz strzałkę **powiązania** .

     Zostanie wyświetlona lista dostępnych źródeł danych.

5. Rozwiń źródło danych, do którego chcesz powiązać, dopóki nie znajdziesz jednego z nich.

     Na przykład jeśli powiążesz się z wartością kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.

6. Wybierz nazwę elementu, z którym ma zostać utworzone powiązanie.

7. W polu **Typ formatu** wybierz format, który ma zostać zastosowany do danych wyświetlanych w kontrolce.

     W każdym przypadku można określić wartość wyświetlaną w kontrolce, jeśli źródło danych zawiera <xref:System.DBNull>. W przeciwnym razie Opcje różnią się nieco w zależności od wybranego typu formatu. W poniższej tabeli przedstawiono typy i opcje formatu.

    |Typ formatu|Opcja formatowania|
    |-----------------|-----------------------|
    |Bez formatowania|Brak opcji.|
    |Numeric|Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .|
    |Waluta|Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .|
    |Data i godzina|Wybierz, w jaki sposób ma być wyświetlana data i godzina, wybierając jeden z elementów w polu wyboru **typu** .|
    |Nauk|Określ liczbę miejsc dziesiętnych przy użyciu funkcji **miejsca dziesiętnego** .|
    |Celnej|Określ niestandardowy ciąg formatujący przy użyciu.<br /><br /> Aby uzyskać więcej informacji, zobacz [Typy formatowania](../../standard/base-types/formatting-types.md). **Uwaga:**  Niestandardowe ciągi formatujące nie są gwarantowane w celu pomyślnej rundy między źródłem danych i kontrolą powiązaną. Zamiast tego obsłużyć <xref:System.Windows.Forms.Binding.Parse> zdarzenie or <xref:System.Windows.Forms.Binding.Format> dla powiązania i zastosować niestandardowe formatowanie w kodzie obsługi zdarzeń.|

8. Wybierz **przycisk OK** , aby zamknąć okno dialogowe **Formatowanie i powiązanie zaawansowane** i wrócić do okno właściwości.

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie prostego formantu powiązanego w formularzu systemu Windows](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Weryfikacja danych użytkownika w formularzach Windows Forms](user-input-validation-in-windows-forms.md)
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
