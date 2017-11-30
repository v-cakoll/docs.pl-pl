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
ms.openlocfilehash: 006cafafdf8e3c3f4da77394d6155fa52e113b58
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/22/2017
---
# <a name="bindingsource-component"></a>BindingSource — Składnik
Hermetyzuje źródło danych dla powiązania kontrolki.  
  
 <xref:System.Windows.Forms.BindingSource> Składnika służy dwóch celów. Po pierwsze zapewnia warstwę pośredników podczas wiązania z danymi formantów w formularzu. Jest to osiągane przez powiązanie <xref:System.Windows.Forms.BindingSource> składnika do źródła danych, a następnie powiązanie formantów w formularzu do <xref:System.Windows.Forms.BindingSource> składnika. Wszystkie dalsze interakcji z danymi, w tym przeglądanie, sortowanie, filtrowanie i aktualizowanie, jest realizowane za pomocą wywołania <xref:System.Windows.Forms.BindingSource> składnika.  
  
 Drugi, <xref:System.Windows.Forms.BindingSource> składnika może działać jako źródło danych jednoznacznie. Dodawanie typów do <xref:System.Windows.Forms.BindingSource> składnik o <xref:System.Windows.Forms.BindingSource.Add%2A> metoda tworzy listę tego typu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Informacje o składniku BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component-overview.md)  
 Ogólne pojęcia związane z <xref:System.Windows.Forms.BindingSource> składnika, dzięki czemu można powiązać źródła danych z formantu.  
  
 [Porady: powiązywanie formantów formularzy systemu Windows wartościami bazy danych DBNull](../../../../docs/framework/winforms/controls/how-to-bind-windows-forms-controls-to-dbnull-database-values.md)  
 Pokazuje sposób obsługi <xref:System.DBNull> wartości z źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [Porady: filtrowanie i sortowanie danych ADO.NET za pomocą składnika BindingSource formularzy systemu Windows](../../../../docs/framework/winforms/controls/sort-and-filter-ado-net-data-with-wf-bindingsource-component.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składnika do zastosowania sortowania i filtrów do wyświetlanych danych.  
  
 [Porady: powiązanie z usługą sieci Web za pomocą formantu BindingSource formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-bind-to-a-web-service-using-the-windows-forms-bindingsource.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.BindingSource> składnik do powiązania z usługą sieci Web.  
  
 [Porady: obsługa błędów i wyjątków występujących za powodu powiązania danych](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składnik, aby obsługiwać błędów występujących w operacji wiązania danych.  
  
 [Porady: powiązanie formantu formularzy systemu Windows z typem](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-type.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, które można powiązać z typem.  
  
 [Porady: powiązanie formantu formularzy systemu Windows z obiektem fabryki](../../../../docs/framework/winforms/controls/how-to-bind-a-windows-forms-control-to-a-factory-object.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, aby powiązać obiekt fabryki lub metody.  
  
 [Porady: dostosowywanie dodawania elementu przy formantu BindingSource formularzy systemu Windows](../../../../docs/framework/winforms/controls/how-to-customize-item-addition-with-the-windows-forms-bindingsource.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników do tworzenia nowych elementów i dodaj je do źródła danych.  
  
 [Porady: wywoływanie powiadomień o zmianie za pomocą metody BindingSource Resetitem](../../../../docs/framework/winforms/controls/how-to-raise-change-notifications-using-the-bindingsource-resetitem-method.md)  
 Pokazuje przy użyciu <xref:System.Windows.Forms.BindingSource> składników, aby wywołać zdarzenia zmiany powiadomienia dla źródeł danych, które nie obsługują powiadomienie o zmianie.  
  
 [Porady: wywoływanie powiadomień o zmianie za pomocą składnika BindingSource i interfejsu INotifyPropertyChanged](../../../../docs/framework/winforms/controls/raise-change-notifications--bindingsource.md)  
 Przedstawiono sposób użycia typu, która dziedziczy <xref:System.ComponentModel.INotifyPropertyChanged> z <xref:System.Windows.Forms.BindingSource> formantu.  
  
 [Porady: odzwierciedlanie aktualizacji źródła danych w formancie formularzy systemu Windows za pomocą elementu BindingSource](../../../../docs/framework/winforms/controls/reflect-data-source-updates-in-a-wf-control-with-the-bindingsource.md)  
 Pokazuje, jak reagować na zmiany w źródła danych przy użyciu <xref:System.Windows.Forms.BindingSource> składnika.  
  
 [Porady: udostępnianie danych powiązanych w wielu formularzach za pomocą składnika BindingSource](../../../../docs/framework/winforms/controls/how-to-share-bound-data-across-forms-using-the-bindingsource-component.md)  
 Przedstawia sposób użycia <xref:System.Windows.Forms.BindingSource> powiązanie wielu formularzy do tego samego źródła danych.  
  
## <a name="reference"></a>Tematy pomocy  
 <xref:System.Windows.Forms.BindingSource>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingSource> składnika.  
  
 <xref:System.Windows.Forms.BindingNavigator>  
 Zawiera dokumentacja referencyjna dla <xref:System.Windows.Forms.BindingNavigator> formantu.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Powiązanie danych formularzy systemu Windows](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 Zawiera łącza do tematów opisujących architektura powiązanie danych formularzy systemu Windows.  
  
 Zobacz też [powiązywanie formantów z danymi w Visual Studio](/visualstudio/data-tools/bind-controls-to-data-in-visual-studio).
