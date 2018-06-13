---
title: 'Porady: tworzenie formantu powiązanego oraz formatowanie wyświetlanych danych'
ms.date: 03/30/2017
helpviewer_keywords:
- data [Windows Forms], formatting
- bound controls [Windows Forms], creating
- bound controls [Windows Forms], formatting data
ms.assetid: d5a56228-899d-41d9-8af8-87b3f4ec2f94
ms.openlocfilehash: 9055ec9c4b646e0c86819e4e72db8ce20086bace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542213"
---
# <a name="how-to-create-a-bound-control-and-format-the-displayed-data"></a>Porady: tworzenie formantu powiązanego oraz formatowanie wyświetlanych danych
Z wiązanie danych formularzy systemu Windows, można sformatować danych wyświetlanych w formancie powiązane z danymi przy użyciu **formatowanie i zaawansowane powiązanie** okno dialogowe.  
  
> [!NOTE]
>  Okna dialogowe i polecenia menu mogą się różnić od tych opisanych w Pomocy, w zależności od ustawień aktywnych lub wydania. Aby zmienić ustawienia, wybierz **Import i eksport ustawień** na **narzędzia** menu. Aby uzyskać więcej informacji, zobacz [Dostosowywanie ustawień środowiska w programie Visual Studio](http://msdn.microsoft.com/library/22c4debb-4e31-47a8-8f19-16f328d7dcd3).  
  
### <a name="to-bind-a-control-and-format-the-displayed-data"></a>Powiązanie formantu i formatowanie wyświetlanych danych  
  
1.  Połączenie ze źródłem danych.  
  
     Aby uzyskać więcej informacji, zobacz [połączenie ze źródłem danych](../../../docs/framework/data/adonet/connecting-to-a-data-source.md).  
  
2.  W formularzu wybierz kontrolkę, a następnie otwórz okno właściwości.  
  
3.  Rozwiń węzeł **(DataBindings)** właściwości, a następnie w **(zaawansowane)** kliknij przycisk wielokropka (![VisualStudioEllipsesButton — zrzut ekranu] (../../../docs/framework/winforms/media/vbellipsesbutton.png " vbEllipsesButton")) do wyświetlenia **formatowanie i zaawansowane powiązanie** okno dialogowe, które zawiera pełną listę właściwości dla tego formantu.  
  
4.  Wybierz właściwość, aby powiązać, a następnie kliknij przycisk **powiązanie** strzałki.  
  
     Zostanie wyświetlona lista dostępnych źródeł danych.  
  
5.  Rozwiń źródło danych, które chcesz powiązać do momentu znalezienia element danych, który ma.  
  
     Na przykład są wiązane wartość kolumny w tabeli zestawu danych, rozwiń nazwę zestawu danych, a następnie rozwiń nazwę tabeli, aby wyświetlić nazwy kolumn.  
  
6.  Kliknij nazwę elementu, aby powiązać.  
  
7.  W **Format typu** kliknij formatu, który chcesz zastosować do danych wyświetlanych w formancie.  
  
     W każdym przypadku można określić wartość wyświetlana w formancie, jeśli źródło danych zawiera <xref:System.DBNull>. W przeciwnym razie wartość opcji się nieco różnić, w zależności od wybranego typu formatu. W poniższej tabeli przedstawiono typy formatu i opcje.  
  
    |Typ formatu|Opcja formatowania|  
    |-----------------|-----------------------|  
    |Bez formatowania|Brak opcji.|  
    |numeryczne|Określ liczbę miejsc dziesiętnych, używając **miejsc dziesiętnych** formantu góra dół.|  
    |Waluta|Określ liczbę miejsc dziesiętnych, używając **miejsc dziesiętnych** formantu góra dół.|  
    |Data i godzina|Wybierz sposób wyświetlania daty i godziny wybranie jednego z elementów w **typu** pola wyboru.|  
    |Naukowe|Określ liczbę miejsc dziesiętnych, używając **miejsc dziesiętnych** formantu góra dół.|  
    |Niestandardowe|Określ ciąg formatu niestandardowego za pomocą.<br /><br /> Aby uzyskać więcej informacji, zobacz [typy formatowania](../../../docs/standard/base-types/formatting-types.md). **Uwaga:** pomyślnie obiegu między źródłem danych a powiązanej Kontrolki niestandardowe ciągi formatów nie ma gwarancji. Obsługi zamiast <xref:System.Windows.Forms.Binding.Parse> lub <xref:System.Windows.Forms.Binding.Format> zdarzenia dla tego powiązania i zastosować niestandardowe formatowanie kodu obsługi zdarzeń.|  
  
8.  Kliknij przycisk **OK** zamknąć **formatowanie i zaawansowane powiązanie** okno dialogowe i wrócić do okna właściwości.  
  
## <a name="see-also"></a>Zobacz też  
 [Instrukcje: tworzenie prostej kontrolki powiązanej na formularzu systemu Windows](../../../docs/framework/winforms/how-to-create-a-simple-bound-control-on-a-windows-form.md)  
 [Weryfikacja danych użytkownika w formularzach Windows Forms](../../../docs/framework/winforms/user-input-validation-in-windows-forms.md)  
 [Wiązanie danych formularzy Windows Forms](../../../docs/framework/winforms/windows-forms-data-binding.md)
