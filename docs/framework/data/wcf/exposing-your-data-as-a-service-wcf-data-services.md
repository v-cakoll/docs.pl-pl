---
title: "Udostępnianie danych jako usługa (usługi danych WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 0c2d664166d9c0b750f6aecf9588a63b8705f0d1
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="exposing-your-data-as-a-service-wcf-data-services"></a>Udostępnianie danych jako usługa (usługi danych WCF)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]integruje się z programem Visual Studio, aby możliwe było łatwiej zdefiniować usług do udostępnienia danych jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródeł danych. Tworzenie usługi danych, który opisuje [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] źródła danych obejmuje następujące podstawowe kroki:  
  
1.  **Zdefiniuj** **modelu danych**. [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]natywnie obsługuje modeli danych, które są oparte na [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]obsługuje także modeli danych, które są oparte na wspólnej języka wspólnego (CLR) obiektów, które zwrócić wystąpienia <xref:System.Linq.IQueryable%601> interfejsu. Dzięki temu można wdrożyć usługi danych, które są oparte na list, tablic i kolekcje w programie .NET Framework. Aby włączyć tworzenie, aktualizowanie i usuwanie operacji za pośrednictwem tych struktur danych, musi także implementować <xref:System.Data.Services.IUpdatable> interfejsu. Aby uzyskać więcej informacji, zobacz [porady: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).  
  
     W przypadku bardziej zaawansowanych scenariuszy [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] zawiera zestaw dostawców, które umożliwiają definiowanie na podstawie typów danych z późnym wiązaniem modelu danych. Aby uzyskać więcej informacji, zobacz [dostawców usług danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).  
  
2.  **Utwórz usługę danych.** Najbardziej podstawowa usługa danych udostępnia klasy, która dziedziczy <xref:System.Data.Services.DataService%601> klasy z typem `T` czyli kwalifikowana przestrzeni nazw nazwa kontenera jednostek. Aby uzyskać więcej informacji, zobacz [definiowania usługi danych WCF](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).  
  
3.  **Skonfiguruj usługę danych.** Domyślnie [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] wyłącza dostęp do zasobów, które są dostępne w kontenerze jednostek. <xref:System.Data.Services.DataServiceConfiguration> Interfejsu można skonfigurować dostęp do zasobów i operacji usługi, określ obsługiwaną wersję [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]oraz innych zachowań usługi WWW, takich jak przetwarzanie wsadowe zachowania lub maksymalna liczba jednostek, które można określić zwracane w pojedynczą odpowiedź. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).  
  
 Na przykład sposobu tworzenia usługi simple danych opartą na bazie danych Northwind zobacz [szybkiego startu](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)  
 [Omówienie](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
