---
title: "BindingSource — Składnik"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- data binding [Windows Forms], Windows Forms
- Windows Forms, data binding control
- BindingSource component [Windows Forms]
ms.assetid: 3e2faf4c-f5b8-4fa6-9fbc-f59c37ec2fb9
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 08b55bc2bd5af78eb6c3d0f5adce3ec39d288a9f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="bindingsource-component"></a>BindingSource — Składnik
Hermetyzuje źródło danych dla powiązania kontrolki.  
  
 <xref:System.Windows.Forms.BindingSource> Składnika służy dwóch celów. Po pierwsze zapewnia warstwę pośredników podczas wiązania z danymi formantów w formularzu. Jest to osiągane przez powiązanie <xref:System.Windows.Forms.BindingSource> składnika do źródła danych, a następnie powiązanie formantów w formularzu do <xref:System.Windows.Forms.BindingSource> składnika. Wszystkie dalsze interakcji z danymi, w tym przeglądanie, sortowanie, filtrowanie i aktualizowanie, jest realizowane za pomocą wywołania <xref:System.Windows.Forms.BindingSource> składnika.  
  
 Drugi, <xref:System.Windows.Forms.BindingSource> składnika może działać jako źródło danych jednoznacznie. Dodawanie typów do <xref:System.Windows.Forms.BindingSource> składnik o <xref:System.Windows.Forms.BindingSource.Add%2A> metoda tworzy listę tego typu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [BindingSource, składnik — omówienie](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 Ogólne pojęcia związane z <xref:System.Windows.Forms.BindingSource> składnika, dzięki czemu można powiązać źródła danych z formantu.  
  
 [Instrukcje: powiązanie kontrolek formularzy Windows Forms z wartościami bazy danych DBNull](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Pokazuje sposób obsługi <xref:System.DBNull> wartości z źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [Instrukcje: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy Windows Forms](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składnika do zastosowania sortowania i filtrów do wyświetlanych danych.  
  
 [Instrukcje: powiązanie z usługą internetową za pomocą kontrolki BindingSource formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.BindingSource> składnik do powiązania z usługą sieci Web.  
  
 [Instrukcje: obsługa błędów i wyjątków występujących za powodu powiązania danych](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składnik, aby obsługiwać błędów występujących w operacji wiązania danych.  
  
 [Instrukcje: powiązanie kontrolki Windows Forms z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, które można powiązać z typem.  
  
 [Instrukcje: powiązanie kontrolki Windows Forms z obiektem fabryki](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, aby powiązać obiekt fabryki lub metody.  
  
 [Instrukcje: dostosowywanie dodawania elementu przy użyciu kontrolki BindingSource formularzy Windows Forms](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników do tworzenia nowych elementów i dodaj je do źródła danych.  
  
 [Instrukcje: wywoływanie powiadomień o zmianie za pomocą metody BindingSource ResetItem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, aby wywołać zdarzenia zmiany powiadomienia dla źródeł danych, które nie obsługują powiadomienie o zmianie.  
  
 [Instrukcje: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 Przedstawiono sposób użycia typu, która dziedziczy <xref:System.ComponentModel.INotifyPropertyChanged> z <xref:System.Windows.Forms.BindingSource> formantu.  
  
 [Instrukcje: odzwierciedlanie aktualizacji źródła danych w kontrolce Windows Forms za pomocą elementu BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Pokazuje, jak reagować na zmiany w źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [Instrukcje: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.BindingSource> powiązanie wielu formularzy do tego samego źródła danych.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.BindingSource>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingSource> składnika.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingNavigator> formantu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Wiązanie danych formularzy Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 Zawiera łącza do tematów opisujących architektura powiązanie danych formularzy systemu Windows.  
  
 Zobacz też [powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
