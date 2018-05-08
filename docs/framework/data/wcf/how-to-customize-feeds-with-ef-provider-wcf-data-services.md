---
title: 'Porady: Dostosowywanie źródła danych za pomocą dostawcy programu Entity Framework (usługi danych WCF)'
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, customizing
- WCF Data Services, customizing feeds
ms.assetid: fd16272e-36f2-415e-850e-8a81f2b17525
ms.openlocfilehash: bd29f6154297c2410294af14952d3d79201966ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-customize-feeds-with-the-entity-framework-provider-wcf-data-services"></a>Porady: Dostosowywanie źródła danych za pomocą dostawcy programu Entity Framework (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Umożliwia dostosowanie Atom serializacji w odpowiedzi usługi danych, dzięki czemu można zamapować właściwości jednostki do nieużywanych elementów, które są zdefiniowane w protokole AtomPub. W tym temacie przedstawiono sposób definiowania atrybutów mapowania dla typów jednostek w modelu danych, która jest zdefiniowana w pliku edmx przy użyciu dostawcy programu Entity Framework. Aby uzyskać więcej informacji, zobacz [źródła danych dostosowywania](../../../../docs/framework/data/wcf/feed-customization-wcf-data-services.md).  
  
 W tym temacie zostaną ręcznie zmodyfikować plik edmx wygenerowany przez narzędzie, który zawiera model danych. Należy ręcznie zmodyfikować plik rozszerzenia do modelu danych nie są obsługiwane przez program Entity Designer. Aby uzyskać więcej informacji o pliku edmx, który generuje narzędzi modelu danych jednostki, zobacz [pliku Przegląd edmx](http://msdn.microsoft.com/library/f4c8e7ce-1db6-417e-9759-15f8b55155d4). Przykład, w tym temacie korzysta z Northwind przykładowych danych wygenerowany automatycznie i usługi klienta danych usługi klas. Ta usługa i klas danych klienta są tworzone po ukończeniu [szybkiego startu usługi danych WCF](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-manually-modify-the-northwindedmx-file-to-add-feed-customization-attributes"></a>Aby ręcznie zmodyfikować plik Northwind.edmx, aby dodać źródła danych dostosowywania atrybutów  
  
1.  W **Eksploratora rozwiązań**, kliknij prawym przyciskiem myszy `Northwind.edmx` pliku, a następnie kliknij przycisk **Otwórz za pomocą**.  
  
2.  W **Otwórz za pomocą - Northwind.edmx** okno dialogowe, wybierz opcję **edytora XML**, a następnie kliknij przycisk **OK**.  
  
3.  Zlokalizuj `ConceptualModels` elementu i Zastąp istniejące `Customers` typu jednostki z następującego elementu, który zawiera źródła danych dostosowywania Mapowanie atrybutów:  
  
     [!code-xml[Astoria Custom Feeds#EdmFeedCustomers](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/northwind.csdl#edmfeedcustomers)]  
  
4.  Zapisz zmiany i zamknij plik Northwind.edmx.  
  
5.  (Opcjonalnie) Kliknij prawym przyciskiem myszy plik Northwind.edmx, a następnie kliknij przycisk **Uruchom narzędzie niestandardowe**.  
  
     To ponowne wygenerowanie pliku warstwy obiektów, które mogą być wymagane.  
  
6.  Skompiluj ponownie projekt.  
  
## <a name="example"></a>Przykład  
 Poprzedni przykład zwraca następujący wyników dla identyfikatora URI `http://myservice/``Northwind.svc/Customers('ALFKI')`.  
  
 [!code-xml[Astoria Custom Feeds#EdmFeedResult](../../../../samples/snippets/xml/VS_Snippets_Misc/astoria custom feeds/xml/edmfeedresult.xml#edmfeedresult)]  
  
## <a name="see-also"></a>Zobacz też  
 [Dostawca programu Entity Framework](../../../../docs/framework/data/wcf/entity-framework-provider-wcf-data-services.md)
