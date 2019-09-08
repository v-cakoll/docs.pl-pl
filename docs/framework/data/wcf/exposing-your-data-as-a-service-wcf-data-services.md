---
title: Uwidacznianie danych jako usługi (Usługi danych programu WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, configuring
- getting started, WCF Data Services
- WCF Data Services, getting started
ms.assetid: df0bbcee-f66f-4a88-abb4-4e73c8b9c908
ms.openlocfilehash: 1dc1f0ec12c50c4c97b141a34b468e3367ead75e
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780302"
---
# <a name="expose-your-data-as-a-service-wcf-data-services"></a>Uwidacznianie danych jako usługi (Usługi danych programu WCF)

Usługi danych programu WCF integruje się z programem Visual Studio, aby ułatwić Ci Definiowanie usług w celu udostępnienia danych [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] jako źródeł. Tworzenie usługi danych, która uwidacznia kanał danych OData, obejmuje następujące podstawowe kroki:

1. **Zdefiniuj model danych.** Usługi danych programu WCF natywnie obsługuje modele danych, które są oparte na [Entity Framework ADO.NET](../adonet/ef/index.md). Aby uzyskać więcej informacji, zobacz [jak: Utwórz usługę danych przy użyciu źródła](create-a-data-service-using-an-adonet-ef-data-wcf.md)danych ADO.NET Entity Framework.

     Usługi danych programu WCF obsługuje również modele danych, które są oparte na obiektach środowiska uruchomieniowego języka wspólnego (CLR), które <xref:System.Linq.IQueryable%601> zwracają wystąpienie interfejsu. Pozwala to na wdrażanie usług danych opartych na listach, tablicach i kolekcjach w .NET Framework. Aby włączyć operacje tworzenia, aktualizowania i usuwania za pośrednictwem tych struktur danych, należy również zaimplementować <xref:System.Data.Services.IUpdatable> interfejs. Aby uzyskać więcej informacji, zobacz [jak: Utwórz usługę danych przy użyciu dostawcy](create-a-data-service-using-rp-wcf-data-services.md)odbicia.

     W przypadku bardziej zaawansowanych scenariuszy Usługi danych programu WCF obejmuje zestaw dostawców, które umożliwiają zdefiniowanie modelu danych na podstawie późnych typów danych. Aby uzyskać więcej informacji, zobacz [niestandardowe dostawcy usług danych](custom-data-service-providers-wcf-data-services.md).

2. **Utwórz usługę danych.** Najbardziej podstawowa usługa danych uwidacznia klasę, która dziedziczy z <xref:System.Data.Services.DataService%601> klasy, z typem `T` , który jest kwalifikowana nazwaną przestrzenią nazw kontenera jednostek. Aby uzyskać więcej informacji, zobacz [definiowanie usługi danych programu WCF](defining-wcf-data-services.md).

3. **Skonfiguruj usługę danych.** Domyślnie Usługi danych programu WCF wyłącza dostęp do zasobów, które są udostępniane przez kontener jednostek. <xref:System.Data.Services.DataServiceConfiguration> Interfejs umożliwia konfigurowanie dostępu do zasobów i usług, określanie obsługiwanej wersji usługi OData oraz definiowanie innych zachowań obejmujących wiele usług, takich jak zachowania wsadowe lub maksymalna liczba jednostek, które mogą zostać zwrócone w pojedynczej odpowiedzi. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usługi danych](configuring-the-data-service-wcf-data-services.md).

Aby zapoznać się z przykładem tworzenia prostej usługi danych opartej na przykładowej bazie danych Northwind, zobacz [Szybki Start](quickstart-wcf-data-services.md).

## <a name="see-also"></a>Zobacz także

- [Wprowadzenie](getting-started-with-wcf-data-services.md)
- [Omówienie](wcf-data-services-overview.md)
