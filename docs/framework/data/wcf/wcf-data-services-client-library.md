---
title: Biblioteka klienta usług danych WCF
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
- DataServiceQuery class, about DataServiceQuery class
- DataServiceContext class, about DataServiceContext class
ms.assetid: 21075e50-8917-413e-a8ea-35a0f6e65aa5
ms.openlocfilehash: e078ba07072f71332aa2f19681b142df946ec391
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975077"
---
# <a name="wcf-data-services-client-library"></a>Biblioteka klienta usług danych WCF
Każda aplikacja może korzystać z usługi danych opartych na protokole Open Data Protocol (OData), jeśli może wysyłać żądanie HTTP i przetwarzać źródło danych OData, które zwraca usługa. To współdziałanie umożliwia dostęp do usług opartych na protokole OData z szerokiego zakresu aplikacji korzystających z sieci Web. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] obejmuje biblioteki klienckie, które zapewniają bogatsze środowisko programistyczne w przypadku korzystania ze źródeł danych OData z aplikacji .NET Framework lub opartych na technologii Silverlight.  
  
 Dwie główne klasy biblioteki klienckiej są klasy <xref:System.Data.Services.Client.DataServiceContext> i klasy <xref:System.Data.Services.Client.DataServiceQuery%601>. Klasa <xref:System.Data.Services.Client.DataServiceContext> hermetyzuje operacje, które są obsługiwane w odniesieniu do określonej usługi danych. Chociaż usługi OData są bezstanowe, kontekst nie jest. W związku z tym można użyć klasy <xref:System.Data.Services.Client.DataServiceContext>, aby zachować stan na kliencie między interakcjami z usługą danych w celu obsługi funkcji, takich jak zarządzanie zmianami. Ta klasa zarządza także tożsamościami i śledzi zmiany. Klasa <xref:System.Data.Services.Client.DataServiceQuery%601> reprezentuje zapytanie względem określonego zestawu jednostek.  
  
 W tej sekcji opisano sposób korzystania z bibliotek klienckich w celu uzyskiwania dostępu do danych i zmiany ich z .NET Framework aplikacji klienckiej. Aby uzyskać więcej informacji na temat używania biblioteki klienta [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] z aplikacją opartą na technologii Silverlight, zobacz [usługi danych programu WCF (Silverlight)](https://go.microsoft.com/fwlink/?LinkId=186016). Dostępne są inne biblioteki klienckie, które umożliwiają korzystanie z kanału informacyjnego OData w innych rodzajach aplikacji. Aby uzyskać więcej informacji, zobacz [zestaw SDK OData](https://go.microsoft.com/fwlink/?LinkID=185796).  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Generowanie biblioteki klienta usługi danych](generating-the-data-service-client-library-wcf-data-services.md)  
 Opisuje sposób generowania klas i bibliotek klienta, które są oparte na źródłach danych OData.  
  
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
 Opisuje sposób powiązania formantów ze strumieniowym źródłem danych OData zwracanym przez usługę.  
  
 [Wywołania operacji usługi](calling-service-operations-wcf-data-services.md)  
 Opisuje, jak używać biblioteki klienckiej do wywoływania operacji usługi.  
  
 [Zarządzanie kontekstem usługi danych](managing-the-data-service-context-wcf-data-services.md)  
 Opisuje opcje zarządzania zachowaniem biblioteki klienta.  
  
 [Praca z danymi binarnymi](working-with-binary-data-wcf-data-services.md)  
 Opisuje, jak uzyskać dostęp do danych binarnych zwracanych przez usługę danych i zmienić je jako strumień danych.  
  
## <a name="see-also"></a>Zobacz także

- [Definiowanie usług danych WCF](defining-wcf-data-services.md)
- [Wprowadzenie](getting-started-with-wcf-data-services.md)
