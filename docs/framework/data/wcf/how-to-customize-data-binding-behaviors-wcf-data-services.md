---
title: 'Instrukcje: Dostosowywanie zachowań powiązań danych (Usługi danych programu WCF)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: c878096cba7d31e0b48727213ee1bb8239b8f690
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790751"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Instrukcje: Dostosowywanie zachowań powiązań danych (Usługi danych programu WCF)
Za [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]pomocą można dostarczyć logikę niestandardową, która jest <xref:System.Data.Services.Client.DataServiceCollection%601> wywoływana przez, gdy obiekt jest dodawany lub usuwany z kolekcji powiązań lub po wykryciu zmiany właściwości. Ta logika niestandardowa jest udostępniana jako <xref:System.Func%602> metody przywoływane jako Delegaty `false` , która zwraca wartość, gdy zachowanie domyślne nadal powinno być wykonywane, gdy `true` Metoda niestandardowa zakończy działanie i podczas kolejnego przetwarzania zdarzenie powinno zostać zatrzymane.  
  
 Przykłady w tym temacie dostarczają niestandardowe metody dla obu `entityChanged` parametrów <xref:System.Data.Services.Client.DataServiceCollection%601>i `entityCollectionChanged` . Przykłady w tym temacie wykorzystują przykładową usługę danych Northwind i automatycznie wygenerowaną klasę usługi danych klienta. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Następująca Strona związana z kodem dla pliku XAML tworzy <xref:System.Data.Services.Client.DataServiceCollection%601> metody z metodami niestandardowymi, które są wywoływane, gdy wystąpią zmiany danych powiązanych z kolekcją powiązań. Gdy wystąpi <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> zdarzenie, podaną metodę uniemożliwiają usunięcie elementu z kolekcji powiązań z usługi danych. Gdy wystąpi `ShipDate` zdarzenie, wartość zostanie sprawdzona, aby upewnić się, że zmiany nie zostały wprowadzone do już dostarczonych zamówień. <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged>  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Przykład  
 Poniższy kod XAML definiuje okno dla poprzedniego przykładu.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](wcf-data-services-client-library.md)
