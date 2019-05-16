---
title: Uwidacznianie danych jako usługa (WCF Data Services)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 0d774db264a02d8d6c752f55344ec1ab6645c0bb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633640"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Uwidacznianie danych jako usługi (WCF Data Services)

Usługi danych WCF jest zintegrowany z programem Visual Studio, aby umożliwić łatwiejsze zdefiniowanie usług, aby uwidocznić dane jako [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] źródła danych. Tworzenie usługi danych, która uwidoczni źródło OData obejmuje następujące podstawowe kroki:

1. **Zdefiniowanie modelu danych.** Usługi danych WCF natywnie obsługuje modele danych, które są oparte na [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md). Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu źródła danych programu ADO.NET Entity Framework](../../../../docs/framework/data/wcf/create-a-data-service-using-an-adonet-ef-data-wcf.md).

     Usługi danych WCF obsługuje również modeli danych, które są na podstawie wspólnego języka wspólnego (CLR) obiektów, które zwracają wystąpienie <xref:System.Linq.IQueryable%601> interfejsu. Pozwala na wdrażanie usług danych, które są oparte na listach, tablice i kolekcje w programie .NET Framework. Aby włączyć tworzenie, aktualizowanie i usuwanie operacji za pośrednictwem tych struktur danych, należy także zaimplementować <xref:System.Data.Services.IUpdatable> interfejsu. Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu dostawcy odbicia](../../../../docs/framework/data/wcf/create-a-data-service-using-rp-wcf-data-services.md).

     Dla bardziej zaawansowanych scenariuszy usługi danych WCF zawiera zestaw dostawców, które umożliwiają zdefiniowanie modelu danych na podstawie typów danych z późnym wiązaniem. Aby uzyskać więcej informacji, zobacz [dostawcy usługi danych niestandardowych](../../../../docs/framework/data/wcf/custom-data-service-providers-wcf-data-services.md).

2. **Tworzenie usługi danych.** Najbardziej podstawowa usługa danych uwidacznia klasę, która dziedziczy po elemencie <xref:System.Data.Services.DataService%601> klasy o typie `T` czyli przestrzeni nazw kwalifikowana nazwa kontenera jednostek. Aby uzyskać więcej informacji, zobacz [Defining WCF Data Services](../../../../docs/framework/data/wcf/defining-wcf-data-services.md).

3. **Skonfiguruj usługę danych.** Domyślnie usługi danych WCF powoduje wyłączenie dostępu do zasobów, które są uwidaczniane przez kontener jednostek. <xref:System.Data.Services.DataServiceConfiguration> Interfejs umożliwia skonfigurowanie dostępu do zasobów i operacji usług, określenie obsługiwanej wersji OData oraz zdefiniowanie innych zachowań całej usługi, takie jak przetwarzanie wsadowe zachowania lub maksymalna liczba jednostek, które mogą być zwracane w jednej odpowiedzi. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md).

Na przykład jak utworzyć usługę danych prostą, opartą na bazie danych Northwind, zobacz [Szybki Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](../../../../docs/framework/data/wcf/getting-started-with-wcf-data-services.md)
- [Omówienie](../../../../docs/framework/data/wcf/wcf-data-services-overview.md)
