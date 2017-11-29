---
title: "&lt;Usuń&gt; elementu &lt;appSettings&gt;"
ms.date: 05/01/2017
ms.prod: .net-framework
ms.technology: dotnet-clr
ms.topic: article
f1_keywords: http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/appSettings/remove
helpviewer_keywords:
- remove Element
- <remove> Element
ms.assetid: 218c4464-e007-4539-803f-7c8b0a909fd8
author: guardrex
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 10202a38d54e4c9744dbd20fb5f226fa41f5dab5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="remove-element-for-appsettings"></a>\<Usuń > elementu \<appSettings >

Usuwa ustawień niestandardowych aplikacji.

[**\<Konfiguracja >**](~/docs/framework/configure-apps/file-schema/configuration-element.md)   
&nbsp;&nbsp;[**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp;**\<Usuń >**

## <a name="syntax"></a>Składnia

```xml
<appSettings>
  <remove key="Key of custom setting" />
</appSettings>
```

### <a name="attribute"></a>Atrybut

|         | Opis |
| ------- | ----------- |
| **klucz** | Atrybut wymagany.<br><br>Określa nazwę klucz do usunięcia. |

### <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<appSettings >**](~/docs/framework/configure-apps/file-schema/appsettings/appsettings-element-for-configuration.md) | Zawiera ustawienia aplikacji niestandardowych, takich jak ścieżki plików, adresy URL usługi XML sieci Web lub inne informacje konfiguracji niestandardowej dla aplikacji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="example"></a>Przykład

Poniższy przykład przedstawia sposób usuwania ustawienia konfiguracji niestandardowej dla `ApplicationName`:

```xml
<appSettings>
  <remove key="ApplicationName" />
</appSettings>
```

## <a name="see-also"></a>Zobacz także

[Schemat pliku konfiguracji dla programu .NET Framework](~/docs/framework/configure-apps/file-schema/index.md)
