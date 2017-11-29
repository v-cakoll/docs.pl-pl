---
title: "Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Forms, data binding
- Windows Forms, adding change notification for data binding
ms.assetid: b5b10f90-0585-41d9-a377-409835262a92
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ffafaff2355e89e2127742f2fba5c005492b4580
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="change-notification-in-windows-forms-data-binding"></a>Powiadomienie o zmianie w powiązaniu danych w formularzach systemu Windows
Jednym z najważniejszych pojęć wiązanie danych formularzy systemu Windows jest *powiadomienie o zmianie*. Aby upewnić się, że źródło danych i formanty powiązane zawsze mieć najnowsze dane, należy dodać powiadomienia o zmianie dla powiązania danych. Aby upewnij się, że formanty powiązane są powiadamiani o zmiany wprowadzone do swojego źródła danych i źródła danych jest powiadamiany o zmiany dokonane w powiązanej właściwości formantu.  
  
 Istnieją różne rodzaje powiadomienia o zmianie, w zależności od rodzaju wiązania z danymi:  
  
-   Proste powiązanie, w którym właściwość jeden formant jest powiązany z pojedynczym wystąpieniem obiektu.  
  
-   Powiązanie oparte na liście, obejmujące właściwości jeden formant powiązany z właściwością element na liście lub właściwości formantu powiązany z listy obiektów.  
  
 Ponadto w przypadku tworzenia formanty formularzy systemu Windows, które ma być używany do wiązania danych, należy najpierw zastosować *PropertyName*zmienić wzorzec do formantów, tak, aby zmiany w powiązanej właściwości formantu są propagowane do źródło danych.  
  
## <a name="change-notification-for-simple-binding"></a>Powiadomienie o zmianie dla powiązania proste  
 Proste powiązanie obiektów biznesowych musi Podaj powiadomienia o zmianie po zmianie wartości właściwości powiązania. Można to zrobić w przypadku wystawianego *PropertyName*zmienione zdarzenie dla każdej właściwości obiekt biznesowy i powiązania obiektu biznesowego do formantów z <xref:System.Windows.Forms.BindingSource> lub preferowaną metodą, w którym zaimplementowano obiekt biznesowy <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu i zgłasza <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenie po zmianie wartości właściwości. Aby uzyskać więcej informacji, zobacz [porady: Implementowanie interfejsu INotifyPropertyChanged](../../../docs/framework/winforms/how-to-implement-the-inotifypropertychanged-interface.md). Jeśli używasz obiektów implementujących <xref:System.ComponentModel.INotifyPropertyChanged> interfejsu, nie trzeba używać <xref:System.Windows.Forms.BindingSource> można powiązać obiektu do formantu, ale przy użyciu <xref:System.Windows.Forms.BindingSource> jest zalecane.  
  
## <a name="change-notification-for-list-based-binding"></a>Powiadomienie o zmianie dla powiązania oparte na liście  
 Formularze systemu Windows zależy od listy powiązanej zapewnienie zmiany właściwości (wprowadzenie zmian wartości właściwości elementu listy) i listy zmienione (element jest usunięte lub dodane do listy) kontrolki powiązane informacje. W związku z tym list używane do wiązania danych musi implementować <xref:System.ComponentModel.IBindingList>, zapewniające obu typów powiadomienia o zmianie. <xref:System.ComponentModel.BindingList%601> Jest implementacją ogólnego <xref:System.ComponentModel.IBindingList> i jest przeznaczony do użytku z wiązanie danych formularzy systemu Windows. Można utworzyć <xref:System.ComponentModel.BindingList%601> zawierający firm typu obiektu, który implementuje <xref:System.ComponentModel.INotifyPropertyChanged> i automatycznie przekonwertuje listy <xref:System.ComponentModel.INotifyPropertyChanged.PropertyChanged> zdarzenia <xref:System.ComponentModel.IBindingList.ListChanged> zdarzenia. Jeśli nie jest powiązane listy <xref:System.ComponentModel.IBindingList>, należy powiązać z listy obiektów do formantów formularzy systemu Windows przy użyciu <xref:System.Windows.Forms.BindingSource> składnika. <xref:System.Windows.Forms.BindingSource> Składnika zapewni podobny do konwersji listy właściwości <xref:System.ComponentModel.BindingList%601>. Aby uzyskać więcej informacji, zobacz [porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md).  
  
## <a name="change-notification-for-custom-controls"></a>Powiadomienie o zmianie w przypadku kontrolek niestandardowych  
 Na koniec, po stronie kontrolki musi ujawniać *PropertyName*zmienione zdarzenie dla każdej właściwości zaprojektowane powiązać dane. Zmiany właściwości formantu są następnie propagowane do źródła danych powiązania. Aby uzyskać więcej informacji, zobacz [porady: stosowanie wzorca PropertyNameChanged](../../../docs/framework/winforms/how-to-apply-the-propertynamechanged-pattern.md)  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Windows.Forms.BindingSource>  
 <xref:System.ComponentModel.INotifyPropertyChanged>  
 <xref:System.ComponentModel.BindingList%601>  
 [Powiązanie danych formularzy systemu Windows](../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Źródła danych obsługiwane przez program Windows Forms](../../../docs/framework/winforms/data-sources-supported-by-windows-forms.md)  
 [Powiązanie danych i formularze systemu Windows](../../../docs/framework/winforms/data-binding-and-windows-forms.md)
