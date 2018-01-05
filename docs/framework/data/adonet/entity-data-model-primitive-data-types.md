---
title: 'Modelu Entity Data Model: Typy danych pierwotnych'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 7635168e-0566-4fdd-8391-7941b0d9f787
caps.latest.revision: "2"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: e9bf1298a5e3fbac82a931abcfb0919238d81bfb
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="entity-data-model-primitive-data-types"></a>Modelu Entity Data Model: Typy danych pierwotnych
Modelu danych jednostki (EDM) obsługuje zestaw typów danych pierwotnych abstrakcyjny (na przykład String, Boolean, Int32 i tak dalej), które są używane do definiowania [właściwości](../../../../docs/framework/data/adonet/property.md) w modelu koncepcyjnym. Te typy danych pierwotnych są serwery proxy dla typów pierwotnych danych rzeczywistych, które są obsługiwane w środowisku macierzystym, takie jak bazy danych programu SQL Server lub środowisko uruchomieniowe języka wspólnego (CLR) lub magazynu. EDM nie definiuje semantykę operacje lub konwersji na typy pierwotne danych; Te semantyki są definiowane przez magazynu lub w środowisku macierzystym. Zazwyczaj typów danych pierwotnych w EDM są mapowane odpowiednie typy pierwotne danych w pamięci masowej lub środowisku macierzystym. Aby uzyskać informacje dotyczące sposobu mapowania programu Entity Framework typów pierwotnych w EDM do typów danych programu SQL Server, zobacz [SqlClient dla jednostki FrameworkTypes](../../../../docs/framework/data/adonet/ef/sqlclient-for-ef-types.md).  
  
> [!NOTE]
>  Nie obsługuje kolekcji typów danych pierwotnych EDM.  
  
 Aby uzyskać informacje o typach danych strukturalnych w EDM, zobacz [typu jednostki](../../../../docs/framework/data/adonet/entity-type.md) i [typu złożonego](../../../../docs/framework/data/adonet/complex-type.md).  
  
## <a name="primitive-data-types-supported-in-the-entity-data-model"></a>Typy pierwotne danych obsługiwane w modelu danych jednostki  
 W poniższej tabeli przedstawiono typy pierwotne danych obsługiwane przez EDM. Podano również [aspekty](../../../../docs/framework/data/adonet/facet.md) który można zastosować do poszczególnych typów danych pierwotnych.  
  
|Typ danych pierwotnych|Opis|Zastosowanie aspektów|  
|-------------------------|-----------------|-----------------------|  
|plików binarnych|Zawiera dane binarne.|Domyślna wartość parametru MaxLength, FixedLength wartości null,|  
|Boolean|Zawiera wartość `true` lub `false`.|Wartości null, domyślny|  
|Byte|Zawiera wartość bez znaku 8-bitową liczbą całkowitą.|Dokładność wartości null, domyślny|  
|DataGodzina|Reprezentuje datę i godzinę.|Dokładność wartości null, domyślny|  
|DateTimeOffset|Zawiera datę i godzinę jako przesunięcie w minutach od GMT.|Dokładność wartości null, domyślny|  
|Wartość dziesiętna|Zawiera wartość liczbową ze stałym precyzję i skalę.|Dokładność wartości null, domyślny|  
|Double|Zawiera zmiennoprzecinkowej numer z dokładnością do 15 cyfr.|Dokładność wartości null, domyślny|  
|Float|Zawiera zmiennoprzecinkowej numer dokładności 7 cyfr.|Dokładność wartości null, domyślny|  
|Identyfikator GUID|Zawiera unikatowy identyfikator 16 bajtów.|Dokładność wartości null, domyślny|  
|Int16|Zawiera wartość całkowita 16-bitowych.|Dokładność wartości null, domyślny|  
|Int32|Zawiera wartość całkowita 32-bitowa.|Dokładność wartości null, domyślny|  
|Int64|Zawiera wartość całkowita 64-bitowa.|Dokładność wartości null, domyślny|  
|SByte|Zawiera wartość całkowita 8-bitowa.|Dokładność wartości null, domyślny|  
|String|Zawiera dane znaków.|Unicode, FixedLength, MaxLength, sortowania, dokładność, wartości null, domyślny|  
|Godzina|Zawiera pora dnia.|Dokładność wartości null, domyślny|  
  
## <a name="see-also"></a>Zobacz też  
 [Kluczowe założenia modelu danych jednostki](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [Model danych jednostki](../../../../docs/framework/data/adonet/entity-data-model.md)
