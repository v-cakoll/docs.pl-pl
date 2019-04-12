---
title: 'Instrukcje: Dostosowywanie zachowania (WCF Data Services) powiązania danych'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, data binding
ms.assetid: 40476b89-8941-4771-8d21-2fe430c85a9d
ms.openlocfilehash: f55c9790b8300a1a3f26e031a17a0982638b562b
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517424"
---
# <a name="how-to-customize-data-binding-behaviors-wcf-data-services"></a>Instrukcje: Dostosowywanie zachowania (WCF Data Services) powiązania danych
Za pomocą [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], możesz podać logikę niestandardową, która jest wywoływana przez <xref:System.Data.Services.Client.DataServiceCollection%601> po dodaniu lub usunięciu z kolekcji powiązania lub w przypadku, gdy zostanie wykryta zmiana właściwości obiektu. Tę logikę niestandardowego jest dostarczana jako metody, określany jako <xref:System.Func%602> delegatów, które zwracają wartość `false` po domyślne zachowanie nadal należy wykonać, po zakończeniu metody niestandardowej i `true` podczas późniejszego przetwarzania powinna zostać zatrzymana, zdarzenia.  
  
 Przykłady w tym temacie dostarczania niestandardowych metod dla obu `entityChanged` i `entityCollectionChanged` parametry <xref:System.Data.Services.Client.DataServiceCollection%601>. Przykłady w tym temacie usługi Northwind przykładowych danych i dane klienta automatycznie wygenerowany usługi klas. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="example"></a>Przykład  
 Tworzy następującą stronę związanym z kodem w pliku XAML <xref:System.Data.Services.Client.DataServiceCollection%601> przy użyciu niestandardowych metod, które są wywoływane, gdy nastąpią zmiany w danych, która jest powiązana z kolekcją powiązania. Gdy <xref:System.Collections.ObjectModel.ObservableCollection%601.CollectionChanged> wystąpi zdarzenie, podana metoda uniemożliwia element, który został usunięty z kolekcji powiązania przed usunięciem z usługi danych. Gdy <xref:System.Collections.ObjectModel.ObservableCollection%601.PropertyChanged> wystąpi zdarzenie, `ShipDate` zweryfikować wartości, aby upewnić się, że nie zostaną wprowadzone zmiany do zamówienia, które już zostały wprowadzone do użytku.  
  
 [!code-csharp[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#wpfdatabindingcustom)]
 [!code-vb[Astoria Northwind Client#WpfDataBindingCustom](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#wpfdatabindingcustom)]  
  
## <a name="example"></a>Przykład  
 Następujące XAML definiuje okna w poprzednim przykładzie.  
  
 [!code-xaml[Astoria Northwind Client#WpfDataBindingCustomXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml#wpfdatabindingcustomxaml)]  
  
## <a name="see-also"></a>Zobacz także

- [Biblioteka klienta usług danych WCF](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
