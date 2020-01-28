---
title: Powiadomienie o zmianie w powiązaniu danych
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
ms.openlocfilehash: 2dffea46bf0db54d28ef55e507767d88bd29ebc2
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746348"
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows
Jednym z najważniejszych koncepcji powiązania danych Windows Forms jest *powiadomienie o zmianie*. Aby upewnić się, że źródło danych i kontrolki powiązane zawsze mają najnowsze dane, musisz dodać powiadomienie o zmianie dla powiązania danych. W celu upewnienia się, że kontrolki powiązane są powiadamiane o zmianach wprowadzonych w źródle danych, a źródło danych jest powiadamiane o zmianach wprowadzonych w powiązanych właściwościach formantu.  
  
 Istnieją różne rodzaje powiadomień o zmianach, w zależności od rodzaju powiązania danych:  
  
- Proste powiązanie, w którym jedna właściwość kontrolki jest powiązana z pojedynczym wystąpieniem obiektu.  
  
- Powiązanie oparte na liście, które może zawierać pojedyncze właściwości kontrolki powiązane z właściwością elementu na liście lub właściwością kontrolki powiązaną z listą obiektów.  
  
 Ponadto w przypadku tworzenia formantów Windows Forms, które mają być używane do wiązania danych, należy zastosować wzorzec zmiany *PropertyName*do kontrolek, tak aby zmiany właściwości powiązanej kontrolki zostały przekazane do źródła danych.  
  
## <a name="change-notification-for-simple-binding"></a>Powiadomienie o zmianie dla prostego powiązania  
 W przypadku prostego powiązania obiekty biznesowe muszą udostępniać powiadomienia o zmianach, gdy wartość właściwości powiązanej ulegnie zmianie. Można to zrobić przez ujawnienie zdarzenia zmiany *PropertyName*dla każdej właściwości obiektu biznesowego i powiązanie obiektu biznesowego z kontrolkami z <xref:System.Windows.Forms.BindingSource> lub preferowaną metodą, w której obiekt biznesowy implementuje interfejs <xref:System.ComponentModel.INotifyPropertyChanged> i wywołuje zdarzenie <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged>, gdy wartość właściwości zostanie zmieniona. Aby uzyskać więcej informacji, zobacz [jak: implementowanie interfejsu INotifyPropertyChanged](how-to-implement-the-inotifypropertychanged-interface.md). Gdy używasz obiektów implementujących interfejs <xref:System.ComponentModel.INotifyPropertyChanged>, nie musisz używać <xref:System.Windows.Forms.BindingSource>, aby powiązać obiekt z kontrolką, ale zaleca się używanie <xref:System.Windows.Forms.BindingSource>.  
  
## <a name="change-notification-for-list-based-binding"></a>Powiadomienie o zmianie dla powiązania opartego na liście  
 Windows Forms zależy od powiązanej listy, aby zapewnić zmianę właściwości (zmiana wartości właściwości elementu listy), a lista została zmieniona (element jest usuwany lub dodawany do listy) do kontrolek powiązanych. W związku z tym listy używane do powiązania danych muszą implementować <xref:System.ComponentModel.IBindingList>, która zapewnia oba typy powiadomień o zmianach. <xref:System.ComponentModel.BindingList%601> to ogólna implementacja <xref:System.ComponentModel.IBindingList> i została zaprojektowana do użycia z powiązaniem danych Windows Forms. Można utworzyć <xref:System.ComponentModel.BindingList%601>, który zawiera typ obiektu biznesowego implementującego <xref:System.ComponentModel.INotifyPropertyChanged>, a lista automatycznie przekonwertuje zdarzenia <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> na zdarzenia <xref:System.ComponentModel.IBindingList.ListChanged>. Jeśli lista powiązania nie jest <xref:System.ComponentModel.IBindingList>, należy powiązać listę obiektów do Windows Forms formantów przy użyciu składnika <xref:System.Windows.Forms.BindingSource>. Składnik <xref:System.Windows.Forms.BindingSource> udostępnia konwersję typu właściwość na listę podobną do tej <xref:System.ComponentModel.BindingList%601>. Aby uzyskać więcej informacji, zobacz [How to: Wywołaj powiadomienia o zmianach za pomocą elementu BindingSource i interfejsu INotifyPropertyChanged](./controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Powiadomienie o zmianie dla kontrolek niestandardowych  
 Na koniec po stronie kontroli należy uwidocznić zdarzenie zmiany *PropertyName*dla każdej właściwości zaprojektowanej do powiązania z danymi. Zmiany właściwości kontrolki są następnie propagowane do powiązanego źródła danych. Aby uzyskać więcej informacji, zobacz [How to: Apply The PropertyNameChanged wzorzec](how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Windows.Forms.BindingSource>
- <xref:System.ComponentModel.INotifyPropertyChanged>
- <xref:System.ComponentModel.BindingList%601>
- [Wiązanie danych formularzy Windows Forms](windows-forms-data-binding.md)
- [Źródła danych obsługiwane przez formularze Windows Forms](data-sources-supported-by-windows-forms.md)
- [Wiązanie danych i formularzy Windows Forms](data-binding-and-windows-forms.md)
