---
title: 'Instrukcje: Dostosowywanie źródła danych za pomocą dostawcy programu Entity Framework (WCF Data Services)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 51e85fa108775806d2c92935868d7ed68534818f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587976"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Instrukcje: Dostosowywanie źródła danych za pomocą dostawcy programu Entity Framework (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia dostosowanie Atom serializacji w odpowiedzi usługi danych, dzięki czemu właściwości jednostki mogą być mapowane do nieużywanych elementów, które są zdefiniowane w protokole AtomPub. W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, która jest zdefiniowana w pliku edmx przy użyciu dostawcy środowiska Entity Framework. Aby uzyskać więcej informacji, zobacz [kanału informacyjnego dostosowywania](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 W tym temacie zostanie ręcznie zmodyfikować plik edmx wygenerowany przez narzędzie, który zawiera model danych. Należy ręcznie zmodyfikować plik, ponieważ rozszerzenia do modelu danych nie są obsługiwane przez projektanta jednostki. Aby uzyskać więcej informacji na temat pliku edmx, które generują narzędzia modelu Entity Data Model, zobacz [Omówienie pliku edmx](https://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4). W przykładzie w tym temacie użyto Northwind przykładowe dane usługi i automatycznie wygenerowany klas usługi danych klienta. Ta usługa i klas danych klienta, są tworzone po ukończeniu [Szybki Start usług danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Aby ręcznie zmodyfikować plik Northwind.edmx, aby dodać atrybuty dostosowywania kanału informacyjnego  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `Northwind.edmx` pliku, a następnie kliknij przycisk **Otwórz za pomocą**.  
  
2.  W **Otwórz za pomocą - Northwind.edmx** okno dialogowe, wybierz opcję **edytora XML**, a następnie kliknij przycisk **OK**.  
  
3.  Znajdź `ConceptualModels` elementu i Zastąp istniejące `Customers` typu jednostki z następujący element, który zawiera źródła danych dostosowywania mapowania atrybutów:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Zapisz zmiany i zamknij plik Northwind.edmx.  
  
5.  (Opcjonalnie) Kliknij prawym przyciskiem myszy plik Northwind.edmx, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
     To ponowne wygenerowanie pliku warstwy obiektu, który może być wymagane.  
  
6.  Skompiluj ponownie projekt.  
  
## <a name="example"></a>Przykład  
 Poprzedni przykład zwraca następujące wyniki dla identyfikatora URI `http://myservice/``Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Zobacz także
- [Dostawca programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
