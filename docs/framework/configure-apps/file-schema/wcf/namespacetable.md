---
title: '&lt;namespaceTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 64801766-01b7-4c65-9ce6-70ad5af67689
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 470dd2dcc2e8554bb89eec159c6b96b24795c5d6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamespacetablegt"></a>&lt;namespaceTable&gt;

Reprezentuje sekcję konfiguracji definiującą zestaw elementów zawierających przestrzeń nazw do mapowania prefiksów, które mogą być następnie używane w filtrach XPath dla routingu.

**\<system.serviceModel >**   
&nbsp;&nbsp;**\<Routing >**   
&nbsp;&nbsp;&nbsp;&nbsp;**\<namespaceTable >**

## <a name="syntax"></a>Składnia

```xml
<system.serviceModel>
  <routing>
    <namespaceTable>
      <add namespace="String" prefix="String" />
    </namespaceTable>
  </routing>
</system.serviceModel>
``` 

## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.

### <a name="attributes"></a>Atrybuty

Brak

### <a name="child-elements"></a>Elementy podrzędne

|     | Opis |
| --- | ----------- |
| [**\<Filtr >**](../../../../../docs/framework/configure-apps/file-schema/wcf/filter.md) | Definiuje mapowanie prefiksu przestrzeni nazw używany dla wyrażenia XPath. |

### <a name="parent-elements"></a>Elementy nadrzędne

|     | Opis |
| --- | ----------- |
| [**\<Routing >**](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md) | Reprezentuje sekcję konfiguracji określającą zestaw filtrów routingu, które określają typ [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] <xref:System.ServiceModel.Dispatcher.MessageFilter> używanego podczas oceniania wiadomości przychodzących, jak również routingu tabel docelowych punktów końcowych do wysyłania komunikatów do podczas definiowania kryteria filtru. |

## <a name="see-also"></a>Zobacz także

<xref:System.ServiceModel.Routing.Configuration.NamespaceElementCollection?displayProperty=nameWithType>
