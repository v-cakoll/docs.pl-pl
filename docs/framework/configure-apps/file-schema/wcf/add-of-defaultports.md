---
title: <add> dla <defaultPorts>
ms.date: 03/30/2017
ms.assetid: f162ce42-963b-4779-96a7-d6d8b4ea0d2f
ms.openlocfilehash: d2723dad14a63c4b05fdb70157f7eb21d193d3ab
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69926707"
---
# <a name="add-of-defaultports"></a>\<Dodawanie > \<defaultPorts >
Domyślny punkt końcowy komunikacji, do którego nasłuchuje aplikacja kliencka.  
  
 \<system.ServiceModel>  
\<> zachowań  
\<serviceBehaviors>  
\<> zachowania  
\<useRequestHeadersForMetadataAddress>  
\<defaultPorts>  
\<add>  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<useRequestHeadersForMetadataAddress>
  <defaultPorts>
    <add port="Integer"
         scheme="String" />
  </defaultPorts>
</useRequestHeadersForMetadataAddress>
```  
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy  
 W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
|Atrybut|Opis|  
|---------------|-----------------|  
|port|Liczba całkowita, która określa domyślny numer portu komunikacyjnego|  
|schemat|Ciąg określający grupę ustawień protokołu skojarzonych z portem komunikacyjnym.|  
  
### <a name="child-elements"></a>Elementy podrzędne  
 Brak.  
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
|Element|Opis|  
|-------------|-----------------|  
|[\<defaultPorts>](defaultports.md)|Kolekcja portów domyślnych wyświetla domyślne punkty końcowe komunikacji, do których nasłuchuje aplikacja kliencka.|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.Configuration.DefaultPortElement>
