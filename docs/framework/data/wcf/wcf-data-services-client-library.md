---
title: "Biblioteka klienta usługi danych WCF"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 1e321200ce4b3582d154c5a188584c9e0b12c10d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="wcf-data-services-client-library"></a>Biblioteka klienta usługi danych WCF
Wszelkie aplikacje mogą współdziałać z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]— na podstawie danych usługi, jeśli może wysłać żądania HTTP i [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych zwracanych usługi danych. Współdziałanie ten umożliwia dostęp do [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]— na podstawie usług z szerokim aplikacje korzystające z zakresu sieci Web. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]zawiera biblioteki klienta, które oferują więcej możliwości programowania, gdy zostaną zużyte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła .NET Framework lub aplikacji opartych na technologii Silverlight.  
  
 Dwie klasy głównym biblioteki klienta są <xref:System.Data.Services.Client.DataServiceContext> klasy i <xref:System.Data.Services.Client.DataServiceQuery%601> klasy. <xref:System.Data.Services.Client.DataServiceContext> Klasa hermetyzuje operacje, które są obsługiwane z usługą określone dane. Mimo że [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] usługi są bezstanowych, kontekst nie jest. W związku z tym można użyć <xref:System.Data.Services.Client.DataServiceContext> klasy do zarządzania stanem na kliencie między interakcji z usługą danych, aby zapewnić obsługę funkcji, takich jak zarządzanie zmianami. Ta klasa również zarządza tożsamości i śledzi zmiany. <xref:System.Data.Services.Client.DataServiceQuery%601> Klasa reprezentuje zapytanie pod kątem określonego zestawu.  
  
 W tej sekcji opisano, jak przy użyciu bibliotek klienta dostępu i zmiany danych z aplikacją kliencką programu .NET Framework. Aby uzyskać więcej informacji o sposobie używania [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Biblioteka klienta oparte na technologii Silverlight aplikacji, zobacz [usługi danych WCF (platformy Silverlight)](http://go.microsoft.com/fwlink/?LinkId=186016). Dostępne są inne biblioteki klienta umożliwiające korzystanie [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych w innych rodzajów aplikacji. Aby uzyskać więcej informacji, zobacz [OData SDK](http://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie biblioteki klienta usługi danych](../../../../docs/framework/data/wcf/generating-the-data-service-client-library-wcf-data-services.md)  
 Opisuje sposób generowania biblioteki klienta i klasy usługi danych klienta, które są oparte na [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródeł danych.  
  
 [Zapytanie usługi danych](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 Opisuje sposób tworzenia zapytań za pomocą biblioteki klienta usługi danych z aplikacji opartych na programie .NET Framework.  
  
 [Ładowanie odłożone zawartości](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)  
 Opisuje sposób załadować dodatkowej zawartości nie jest uwzględniony w odpowiedzi na zapytanie początkowej.  
  
 [Aktualizowanie usługi danych](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 Opisuje sposób tworzenia, modyfikowania i usuwania jednostki i relacje za pomocą biblioteki klienta.  
  
 [Operacje asynchroniczne](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 Zawiera opis funkcji podana przez klienta biblioteki do pracy z usługą danych w sposób asynchroniczny.  
  
 [Przetwarzanie wsadowe operacji](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)  
 Opisuje sposób wysyłania wielu żądań do usługi danych w jednej serii za pomocą biblioteki klienta.  
  
 [Powiązanie danych z formantami](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)  
 Opisuje sposób wiązania kontrolki [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] zwrócony przez usługę danych źródła danych.  
  
 [Wywołania operacji usługi](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)  
 Opisuje sposób korzystania z biblioteki klienta do wywołania operacji usługi.  
  
 [Zarządzanie kontekstu usługi danych](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)  
 Opisuje opcje zarządzania zachowanie biblioteki klienta.  
  
 [Praca z danych binarnych](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md)  
 Opisuje sposób dostępu i zmiany danych binarnych zwrócony przez usługę do dane jako strumienia danych.  
  
## <a name="see-also"></a>Zobacz też  
 [Definiowanie usługi danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md)  
 [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
