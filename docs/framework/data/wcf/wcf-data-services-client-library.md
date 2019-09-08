---
title: Biblioteka klienta usług danych WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: 545442b0086361c8ce8c0482801afc10b1fee96e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70779683"
---
# <a name="wcf-data-services-client-library"></a>Biblioteka klienta usług danych WCF
Każda aplikacja może współistnieć z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]usługą danych opartą na usłudze, jeśli może wysłać żądanie HTTP i [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] przetworzyć kanał informacyjny zwracanej przez usługę danych. To współdziałanie pozwala na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]dostęp do usług opartych na sieci Web w szerokim zakresie. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera biblioteki klienckie, które zapewniają bogatsze środowisko programistyczne w przypadku [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] korzystania ze źródeł danych z aplikacji .NET Framework lub opartych na technologii Silverlight.  
  
 Dwie główne klasy biblioteki klienckiej są <xref:System.Data.Services.Client.DataServiceContext> klasy <xref:System.Data.Services.Client.DataServiceQuery%601> i klasy. <xref:System.Data.Services.Client.DataServiceContext> Klasa hermetyzuje operacje, które są obsługiwane w odniesieniu do określonej usługi danych. Chociaż [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi są bezstanowe, kontekst nie jest. Z tego względu można użyć <xref:System.Data.Services.Client.DataServiceContext> klasy do utrzymania stanu na kliencie między interakcjami z usługą danych w celu obsługi funkcji, takich jak zarządzanie zmianami. Ta klasa zarządza także tożsamościami i śledzi zmiany. <xref:System.Data.Services.Client.DataServiceQuery%601> Klasa reprezentuje zapytanie względem określonego zestawu jednostek.  
  
 W tej sekcji opisano sposób korzystania z bibliotek klienckich w celu uzyskiwania dostępu do danych i zmiany ich z .NET Framework aplikacji klienckiej. Aby uzyskać więcej informacji o sposobach korzystania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z biblioteki klienta z aplikacją opartą na technologii Silverlight, zobacz [usługi danych programu WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Dostępne są inne biblioteki klienckie, które umożliwiają korzystanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z kanału informacyjnego w innych rodzajach aplikacji. Aby uzyskać więcej informacji, zobacz [zestaw SDK OData](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md)  
 Opisuje sposób generowania klas i bibliotek klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródłach danych.  
  
 [Wykonywanie zapytań do usługi danych](querying-the-data-service-wcf-data-services.md)  
 Opisuje sposób wykonywania zapytań do usługi danych z aplikacji opartej na .NET Framework przy użyciu bibliotek klienckich.  
  
 [Ładowanie odroczonej zawartości](loading-deferred-content-wcf-data-services.md)  
 Opisuje sposób ładowania dodatkowej zawartości, która nie jest uwzględniona w początkowej odpowiedzi na zapytanie.  
  
 [Aktualizacja usługi danych](updating-the-data-service-wcf-data-services.md)  
 Opisuje, jak tworzyć, modyfikować i usuwać jednostki i relacje przy użyciu bibliotek klienckich.  
  
 [Operacje asynchroniczne](asynchronous-operations-wcf-data-services.md)  
 Opisuje funkcje udostępniane przez biblioteki klienckie do pracy z usługą danych w sposób asynchroniczny.  
  
 [Operacje przetwarzania wsadowego](batching-operations-wcf-data-services.md)  
 Opisuje sposób wysyłania wielu żądań do usługi danych w pojedynczej partii przy użyciu bibliotek klienckich.  
  
 [Wiązanie danych do kontrolki](binding-data-to-controls-wcf-data-services.md)  
 Opisuje sposób powiązania formantów ze [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] strumieniowym źródłem danych.  
  
 [Wywołania operacji usługi](calling-service-operations-wcf-data-services.md)  
 Opisuje, jak używać biblioteki klienckiej do wywoływania operacji usługi.  
  
 [Zarządzanie kontekstem usługi danych](managing-the-data-service-context-wcf-data-services.md)  
 Opisuje opcje zarządzania zachowaniem biblioteki klienta.  
  
 [Praca z danymi binarnymi](working-with-binary-data-wcf-data-services.md)  
 Opisuje, jak uzyskać dostęp do danych binarnych zwracanych przez usługę danych i zmienić je jako strumień danych.  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Wprowadzenie](getting-started-with-wcf-data-services.md)
