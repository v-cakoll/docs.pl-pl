---
title: 'Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 0f56fc5fa345cbe4584b61ae2622dfb0dfb35be8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59225537"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Instrukcje: Tworzenie kontrolki powiązanej oraz formatowanie wyświetlanych danych
Za pomocą powiązanie danych formularzy Windows, możesz sformatować dane wyświetlane w kontrolce powiązanych z danymi za pomocą **formatowanie i zaawansowane powiązanie** okno dialogowe.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić swoje ustawienia, wybierz opcję **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [personalizowanie środowiska IDE programu Visual Studio](/visualstudio/ide/personalizing-the-visual-studio-ide).  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Aby powiązać formant oraz formatowanie wyświetlanych danych  
  
1.  Łączenie ze źródłem danych.  
  
     Aby uzyskać więcej informacji, zobacz [nawiązania połączenia ze źródłem danych](../data/adonet/connecting-to-a-data-source.md).  
  
2.  W formularzu wybierz kontrolkę, a następnie otwórz okno właściwości.  
  
3.  Rozwiń **(powiązania danych)** właściwości, a następnie w polu **(zaawansowane)** polu i kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu](./media/vbellipsesbutton.png " vbEllipsesButton")) do wyświetlenia **formatowanie i powiązywanie zaawansowane** okno dialogowe, które zawiera pełną listę właściwości dla tej kontrolki.  
  
4.  Wybierz właściwość, aby powiązać, a następnie kliknij przycisk **powiązanie** strzałki.  
  
     Zostanie wyświetlona lista dostępnych źródeł danych.  
  
5.  Rozwiń źródło danych, które chcesz powiązać, dopóki nie znajdziesz element danych jednego, który ma.  
  
     Na przykład jeśli dokonywane jest wiązanie wartość kolumny w tabeli zestawu danych, rozwiń węzeł z nazwą zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.  
  
6.  Kliknij nazwę elementu można powiązać.  
  
7.  W **sformatować typu** kliknij format, w którym chcesz zastosować do danych wyświetlanych w formancie.  
  
     W każdym przypadku można określić wartości wyświetlanej w kontrolce, jeśli źródło danych zawiera <xref:System.DBNull>. W przeciwnym razie różne opcje nieco w zależności od wybranego typu formatu. W poniższej tabeli przedstawiono typy formatów i opcje.  
  
    |Typ formatu|Opcja formatowania|  
    |-----------------|-----------------------|  
    |Bez formatowania|Brak opcji.|  
    |Numeryczne|Określ liczbę miejsc dziesiętnych, za pomocą **miejsc dziesiętnych** formantu góra dół.|  
    |Waluta|Określ liczbę miejsc dziesiętnych, za pomocą **miejsc dziesiętnych** formantu góra dół.|  
    |Data i godzina|Wybierz sposób wyświetlania daty i godziny, wybierając jeden z elementów w **typu** pola wyboru.|  
    |naukowe|Określ liczbę miejsc dziesiętnych, za pomocą **miejsc dziesiętnych** formantu góra dół.|  
    |Niestandardowe|Określ ciąg formatu niestandardowego za pomocą.<br /><br /> Aby uzyskać więcej informacji, zobacz [typy formatowania](../../standard/base-types/formatting-types.md). **Uwaga:**  Tworzenie niestandardowych formatów ciągów nie ma gwarancji pomyślnie komunikacji dwustronnej między źródłem danych i powiązanej kontrolki. Zamiast tego obsługiwać <xref:System.Windows.Forms.Binding.Parse> lub <xref:System.Windows.Forms.Binding.Format> zdarzeń dla wiązania i zastosować niestandardowe formatowanie w kodzie obsługi zdarzeń.|  
  
8.  Kliknij przycisk **OK** zamknąć **formatowanie i powiązywanie zaawansowane** okno dialogowe i wrócić do okna właściwości.  
  
## <a name="see-also"></a>Zobacz także

- [Instrukcje: Tworzenie prostej kontrolki powiązanej na formularzu Windows Form](how-to-create-a-simple-bound-control-on-a-windows-form.md)
- [Walidacja danych użytkownika w formularzach systemu Windows](user-input-validation-in-windows-forms.md)
- [Powiązywanie danych formularzy systemu Windows](windows-forms-data-binding.md)
