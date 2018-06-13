---
title: 'Porady: dostosowywanie zachowania (usługi danych WCF) powiązanie danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: 6ebc50a4a4ed2c91db0dcbcb53d3965757a94f9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33364142"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Porady: dostosowywanie zachowania (usługi danych WCF) powiązanie danych
Z [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], możesz podać logiki niestandardowej, która jest wywoływana przez <xref:System.Data.Services.Client.DataServiceCollection%601> po dodaniu lub usunięciu z kolekcji powiązanie lub po wykryciu zmiany właściwości obiektu. Tej niestandardowej logiki jest dostarczane jako metody, określany jako <xref:System.Func%602> delegatów, które zwracają wartość `false` kiedy domyślne zachowanie powinno się odbywać nadal po zakończeniu niestandardowej metody i `true` podczas kolejnych przetwarzanie zdarzenia powinna zostać zatrzymana.  
  
 Przykłady w tym temacie dostarczania niestandardowych metod dla obu `entityChanged` i `entityCollectionChanged` parametry <xref:System.Data.Services.Client.DataServiceCollection%601>. Przykłady w tym temacie usługę Northwind przykładowych danych i dane klienta automatycznie wygenerowaną usługi klasy. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Tworzy następującą stronę CodeBehind dla pliku XAML <xref:System.Data.Services.Client.DataServiceCollection%601> za pomocą metod niestandardowego wywoływane w przypadku wystąpienia zmian do danych, który jest powiązany z kolekcją powiązania. Gdy <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> wystąpi zdarzenie, podana metoda uniemożliwia elementu, który został usunięty z kolekcji powiązanie usunięcie z usługi danych. Gdy <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> wystąpi zdarzenie, `ShipDate` zweryfikować wartości, aby upewnić się, że nie zostaną wprowadzone zmiany do zlecenia, które zostały już wysłane.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Przykład  
 Następujące XAML definiuje okna w poprzednim przykładzie.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Zobacz też  
 [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
