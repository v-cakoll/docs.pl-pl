---
title: BindingSource — Składnik
ms.date: 03/30/2017
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
ms.openlocfilehash: 54639edb512a8bc6c5909282d5e4c210439e2a6e
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/09/2019
ms.locfileid: "57717599"
---
# <a name="bindingsource-component"></a>BindingSource — Składnik
Hermetyzuje źródła danych dla powiązania kontrolki.  
  
 <xref:System.Windows.Forms.BindingSource> Składnika służy do dwóch celów. Po pierwsze zapewnia warstwę operatorów pośrednich podczas tworzenia wiązania kontrolek w formularzu do danych. Jest to realizowane przez powiązanie <xref:System.Windows.Forms.BindingSource> do źródła danych, a następnie powiązanie kontrolek w formularzu do <xref:System.Windows.Forms.BindingSource> składnika. Wszystkie dalszej interakcji z dane, w tym przeglądanie, sortowanie, filtrowanie i aktualizowaniem odbywa się przy użyciu wywołań <xref:System.Windows.Forms.BindingSource> składnika.  
  
 Drugi <xref:System.Windows.Forms.BindingSource> składnika może działać jako źródło silnie typizowanych danych. Dodawanie typu <xref:System.Windows.Forms.BindingSource> składnika za pomocą <xref:System.Windows.Forms.BindingSource.Add%2A> metoda tworzy listę tego typu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [BindingSource, składnik — omówienie](bindingsource-component-overview.md)  
 Ogólne pojęcia związane z <xref:System.Windows.Forms.BindingSource> składnik, który pozwala powiązać źródła danych z kontrolką.  
  
 [Instrukcje: Powiązywanie kontrolek formularzy Windows Forms bazy danych DBNull](how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Pokazuje, jak obsługiwać <xref:System.DBNull> wartości ze źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [Instrukcje: Sortowanie i filtrowanie danych ADO.NET za pomocą Windows składnika BindingSource formularzy](sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnika, aby zastosować sortuje i filtruje do wyświetlanych danych.  
  
 [Instrukcje: Powiązanie z usługą sieci Web przy użyciu kontrolki BindingSource formularzy Windows Forms](how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Ilustruje sposób używania <xref:System.Windows.Forms.BindingSource> składnika do utworzenia powiązania z usługą sieci Web.  
  
 [Instrukcje: Obsługa błędów i wyjątków występujących za powodu powiązania danych](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnik do poprawnego działania obsługi błędów występujących w operacji wiązania danych.  
  
 [Instrukcje: Powiązanie z typem formantu Windows Forms](how-to-bind-a-windows-forms-control-to-a-type.md)  
 Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnika powiązanie z typem.  
  
 [Instrukcje: Powiąż formant programu Windows Forms z obiektem fabryki](how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnika, aby powiązać obiekt fabryki lub metody.  
  
 [Instrukcje: Dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy Windows Forms](how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składników do tworzenia nowych elementów i dodać je do źródła danych.  
  
 [Instrukcje: Wywoływanie powiadomień o zmianie za BindingSource Resetitem](how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Demonstruje użycie <xref:System.Windows.Forms.BindingSource> składnik, aby wywoływać zdarzenia, powiadomienia o zmianie dla źródeł danych, które nie obsługują powiadomienie o zmianie.  
  
 [Instrukcje: Wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](raise-change-notifications--bindingsource.md)  
 Pokazuje, jak używać typu, który dziedziczy z <xref:System.ComponentModel.INotifyPropertyChanged> z <xref:System.Windows.Forms.BindingSource> kontroli.  
  
 [Instrukcje: Odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms przy użyciu kontrolki BindingSource](reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Pokazuje, jak reagować na zmiany źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [Instrukcje: Udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource](how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Ilustruje sposób używania <xref:System.Windows.Forms.BindingSource> powiązanie wielu formularzy do tego samego źródła danych.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.BindingSource>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.BindingSource> składnika.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Zawiera dokumentację referencyjną dla <xref:System.Windows.Forms.BindingNavigator> kontroli.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wiązanie danych formularzy Windows Forms](../windows-forms-data-binding.md)  
 Zawiera łącza do tematów opisujących architektura powiązanie danych formularzy Windows.  
  
 Zobacz też [powiązywanie kontrolek z danymi w programie Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
