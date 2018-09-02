---
title: Biblioteka klienta usług danych WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 4f389530b287d1c7a11a88972ef948347d3ea533
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43421598"
---
# <a name="wcf-data-services-client-library"></a>Biblioteka klienta usług danych WCF
Każda aplikacja może współdziałać z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]— na podstawie danych usługi, jeśli jest w stanie wysyłać żądania HTTP i [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych zwracanych usługi danych. Takie współdziałanie pozwala uzyskać dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usług z szerokim aplikacje korzystające z zakresu sieci Web. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zawiera biblioteki klienckie, które zapewniają bardziej zaawansowane środowisko programowania, gdy wykorzystasz [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł z .NET Framework lub aplikacji opartych na technologii Silverlight.  
  
 Są dwie główne klasy z biblioteki klienta <xref:System.Data.Services.Client.DataServiceContext> klasy i <xref:System.Data.Services.Client.DataServiceQuery%601> klasy. <xref:System.Data.Services.Client.DataServiceContext> Klasa hermetyzuje operacje, które są obsługiwane przez usługę określone dane. Mimo że [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usług są bezstanowe, kontekst nie jest. W związku z tym, można użyć <xref:System.Data.Services.Client.DataServiceContext> klasy do zarządzania stanem na kliencie interakcji z usługi danych w celu obsługi funkcji, takich jak zarządzanie zmianami. Ta klasa również zarządza tożsamości i śledzenie zmian. <xref:System.Data.Services.Client.DataServiceQuery%601> Klasa reprezentuje zapytanie względem zestawu określonej jednostki.  
  
 W tej sekcji opisano, jak wykorzystać biblioteki klienckie dostępu i zmiany danych z aplikacji klienckiej .NET Framework. Aby uzyskać więcej informacji o sposobie używania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Zobacz Biblioteka klienta w przypadku aplikacji opartych na technologii Silverlight [usług danych WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Dostępne są inne biblioteki klienckie umożliwiające używanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w innych rodzajów aplikacji. Aby uzyskać więcej informacji, zobacz [OData SDK](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Opisuje sposób wygenerować bibliotekę klienta i klas usługi danych klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych.  
  
 [Wykonywanie zapytań do usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 W tym artykule opisano sposób tworzenia zapytań względem usługi danych z aplikacji opartych na programie .NET Framework za pomocą biblioteki klienta.  
  
 [Ładowanie odroczonej zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 W tym artykule opisano sposób ładowania dodatkowej zawartości, które nie są uwzględnione w odpowiedzi na zapytanie początkowej.  
  
 [Aktualizacja usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Opisuje sposób tworzenia, modyfikacji i usuwania jednostek i relacji za pomocą biblioteki klienta.  
  
 [Operacje asynchroniczne](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 W tym artykule opisano możliwości udostępniane przez biblioteki klienckie do pracy z usługą danych w sposób asynchroniczny.  
  
 [Operacje przetwarzania wsadowego](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 W tym artykule opisano sposób wysyłania wielu żądań do usługi danych w jednej partii przy użyciu biblioteki klienta.  
  
 [Wiązanie danych do kontrolki](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Opis sposobu tworzenia powiązania kontrolki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródło danych zwróconych przez usługę danych.  
  
 [Wywołania operacji usługi](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 W tym artykule opisano, jak używać biblioteki klienta do wywołania operacji usługi.  
  
 [Zarządzanie kontekstem usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 W tym artykule opisano opcje zarządzania zachowanie biblioteki klienta.  
  
 [Praca z danymi binarnymi](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Informacje dotyczące dostępu i zmiany danych binarnych zwracane przez usługę danych jako strumień danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usług danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
