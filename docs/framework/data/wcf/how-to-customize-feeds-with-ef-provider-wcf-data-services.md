---
title: 'Instrukcje: Dostosowywanie kanałów informacyjnych za pomocą dostawcy Entity Framework (Usługi danych programu WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: 8f994065ea42d6fc522fa297cafa8c46a8164e67
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780153"
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Instrukcje: Dostosowywanie kanałów informacyjnych za pomocą dostawcy Entity Framework (Usługi danych programu WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umożliwia dostosowanie serializacji Atom w odpowiedzi usługi danych, tak aby właściwości jednostki mogły być mapowane do nieużywanych elementów, które są zdefiniowane w protokole AtomPub. W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, który jest zdefiniowany w pliku edmx przy użyciu dostawcy Entity Framework. Aby uzyskać więcej informacji, zobacz temat [Dostosowywanie kanału informacyjnego](feed-customization-wcf-data-services.md).  
  
 W tym temacie utworzysz ręcznie wygenerowany przez narzędzie plik EDMX, który zawiera model danych. Należy ręcznie zmodyfikować plik, ponieważ rozszerzenia do modelu danych nie są obsługiwane przez Entity Designer. Aby uzyskać więcej informacji na temat pliku. edmx wygenerowanego przez narzędzia Entity Data Model, zobacz [plik. edmx Entity Framework — Omówienie](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/cc982042(v=vs.100)). W przykładzie w tym temacie jest stosowana usługa danych przykładowych Northwind i klasy usługi danych klientów. Ta usługa i klasy danych klienta są tworzone po zakończeniu [usługi danych programu WCF szybkiego startu](quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Aby ręcznie zmodyfikować plik Northwind. edmx w celu dodania atrybutów dostosowania kanału informacyjnego  
  
1. W **Eksplorator rozwiązań**kliknij prawym przyciskiem `Northwind.edmx` myszy plik, a następnie kliknij polecenie **Otwórz za pomocą**.  
  
2. W oknie dialogowym **Otwórz za pomocą — Northwind. edmx** wybierz pozycję **Edytor XML**, a następnie kliknij przycisk **OK**.  
  
3. Znajdź element i Zastąp istniejący `Customers` typ jednostki następującym elementem, który zawiera atrybuty mapowania elementu kanału informacyjnego: `ConceptualModels`  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4. Zapisz zmiany i zamknij plik Northwind. edmx.  
  
5. Obowiązkowe Kliknij prawym przyciskiem myszy plik Northwind. edmx, a następnie kliknij polecenie **Uruchom narzędzie niestandardowe**.  
  
     Spowoduje to ponowne wygenerowanie pliku warstwy obiektów, który może być wymagany.  
  
6. Ponownie skompiluj projekt.  
  
## <a name="example"></a>Przykład  
 Poprzedni przykład zwraca Poniższy wynik dla identyfikatora URI `http://myservice/Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria_custom_feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Zobacz także

- [Dostawca programu Entity Framework](entity-framework-provider-wcf-data-services.md)
