---
title: Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 559cdee1cce84df1c4b838e249d11ba235a0c636
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59097580"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows
Jednym z najważniejszych pojęć powiązanie danych formularzy Windows jest *powiadomienie o zmianie*. Aby upewnij się, że źródło danych i formanty powiązane zawsze najnowsze dane, należy dodać powiadomienia o zmianie dla powiązania danych. Aby mieć pewność, że formanty powiązane są powiadamiani o zmianach wprowadzonych do swojego źródła danych i źródła danych jest powiadamiany o zmianach wprowadzonych do powiązanych właściwości kontrolki.  
  
 Istnieją różne rodzaje powiadomienie o zmianie w zależności od rodzaju powiązania danych:  
  
-   Proste powiązanie danych, w którym właściwość jeden formant jest powiązany z pojedynczym wystąpieniem obiektu.  
  
-   Oparte na liście powiązania, który może zawierać właściwości jeden formant powiązany z właściwości elementu na liście lub właściwości kontrolki powiązane z listy obiektów.  
  
 Ponadto w przypadku tworzenia formantów Windows Forms, które chcesz użyć dla powiązania danych, należy najpierw zastosować *PropertyName*zmienione wzorca dla formantów, aby zmiany właściwości powiązanej kontrolki są propagowane do źródło danych.  
  
## <a name="change-notification-for-simple-binding"></a>Powiadomienia o zmianach dotyczącego proste powiązanie  
 Proste powiązanie obiektów biznesowych trzeba podać powiadomienie o zmianie po zmianie wartości właściwości powiązanej. Można to zrobić, zapewniając *PropertyName*zmieniono zdarzenia dla każdej właściwości obiektu biznesowych i powiązanie kontrolek z obiektem biznesowym <xref:System.Windows.Forms.BindingSource> lub preferowaną metodę, w którym implementuje obiekt biznesowy <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenie po zmianie wartości właściwości. Aby uzyskać więcej informacji, zobacz [jak: Implementowanie interfejsu INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md). Kiedy używać obiektów, które implementują <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu, nie trzeba używać <xref:System.Windows.Forms.BindingSource> można powiązać obiektu do formantu, ale przy użyciu <xref:System.Windows.Forms.BindingSource> jest zalecane.  
  
## <a name="change-notification-for-list-based-binding"></a>Powiadomienie o zmianie dla powiązania oparte na liście  
 Windows Forms zależy od powiązana lista umożliwia zmienianie właściwości (zmiany wartości właściwości elementu listy) i zmienić listę (element jest usunięty lub dodane do listy) informacji do kontrolki powiązania. W związku z tym, używany do wiązania danych listy musi implementować <xref:System.ComponentModel.IBindingList>, który zawiera oba rodzaje powiadomienie o zmianie. <xref:System.ComponentModel.BindingList%601> Jest ogólną implementację <xref:System.ComponentModel.IBindingList> i jest przeznaczony do użytku z powiązanie danych formularzy Windows. Możesz utworzyć <xref:System.ComponentModel.BindingList%601> zawierający firm typ obiektu, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i listy zostanie automatycznie przekonwertowana <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia <xref:System.ComponentModel.IBindingList.ListChanged> zdarzenia. Jeśli nie jest powiązana lista <xref:System.ComponentModel.IBindingList>, trzeba będzie powiązać z listy obiektów przeznaczonych do kontrolek formularzy Windows Forms przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. <xref:System.Windows.Forms.BindingSource> Składnika zapewni podobny do konwersji listy właściwości <xref:System.ComponentModel.BindingList%601>. Aby uzyskać więcej informacji, zobacz [jak: Wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Powiadomienie o zmianie w przypadku kontrolek niestandardowych  
 Na koniec po stronie sterowania należy ujawnić *PropertyName*zmieniono zdarzenia dla każdej właściwości, które mają być powiązane z danymi. Zmiany właściwości kontrolki, następnie są propagowane do źródła powiązane dane. Aby uzyskać więcej informacji, zobacz [jak: Stosowanie wzorca PropertyNameChanged](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
- [Źródła danych obsługiwane przez formularze Windows Forms](data-sources-supported-by-windows-forms.md)
- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
