---
title: Uwidacznianie danych jako usługi (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 71f26d7d41d112e13e6a77f0927c61d51b176b27
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73975305"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Uwidacznianie danych jako usługi (Usługi danych programu WCF)

Usługi danych programu WCF integruje się z programem Visual Studio, dzięki czemu można łatwiej definiować usługi, aby uwidaczniać dane jako źródła protokołu Open Data Protocol (OData). Tworzenie usługi danych, która uwidacznia kanał danych OData, obejmuje następujące podstawowe kroki:

1. **Zdefiniuj model danych.** Usługi danych programu WCF natywnie obsługuje modele danych, które są oparte na [Entity Framework ADO.NET](../adonet/ef/index.md). Aby uzyskać więcej informacji, zobacz [jak: Tworzenie usługi danych przy użyciu źródła danych ADO.NET Entity Framework](create-a-data-service-using-an-adonet-ef-data-wcf.md).

     Usługi danych programu WCF obsługuje również modele danych, które są oparte na obiektach środowiska uruchomieniowego języka wspólnego (CLR), które zwracają wystąpienie interfejsu <xref:System.Linq.IQueryable%601>. Pozwala to na wdrażanie usług danych opartych na listach, tablicach i kolekcjach w .NET Framework. Aby włączyć operacje tworzenia, aktualizowania i usuwania za pośrednictwem tych struktur danych, należy również zaimplementować interfejs <xref:System.Data.Services.IUpdatable>. Aby uzyskać więcej informacji, zobacz [How to: Create a Data Service przy użyciu dostawcy odbicia](create-a-data-service-using-rp-wcf-data-services.md).

     W przypadku bardziej zaawansowanych scenariuszy Usługi danych programu WCF obejmuje zestaw dostawców, które umożliwiają zdefiniowanie modelu danych na podstawie późnych typów danych. Aby uzyskać więcej informacji, zobacz [niestandardowe dostawcy usług danych](custom-data-service-providers-wcf-data-services.md).

2. **Utwórz usługę danych.** Najbardziej podstawowa usługa danych uwidacznia klasę, która dziedziczy z klasy <xref:System.Data.Services.DataService%601>, z typem `T`, który jest kwalifikowana nazwa przestrzeni nazw kontenera jednostek. Aby uzyskać więcej informacji, zobacz [definiowanie usługi danych programu WCF](defining-wcf-data-services.md).

3. **Skonfiguruj usługę danych.** Domyślnie Usługi danych programu WCF wyłącza dostęp do zasobów, które są udostępniane przez kontener jednostek. Interfejs <xref:System.Data.Services.DataServiceConfiguration> umożliwia konfigurowanie dostępu do zasobów i usług, określanie obsługiwanej wersji protokołu OData oraz definiowanie innych zachowań dotyczących całej usługi, takich jak zachowania wsadowe lub maksymalna liczba jednostek, które mogą być zwracane w pojedynczej odpowiedzi. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

Aby zapoznać się z przykładem tworzenia prostej usługi danych opartej na przykładowej bazie danych Northwind, zobacz [Szybki Start](quickstart-wcf-data-services.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started-with-wcf-data-services.md)
- [Omówienie](wcf-data-services-overview.md)
