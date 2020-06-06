---
title: <linkedConfiguration>, element
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/assemblyBinding/linkedConfiguration
- http://schemas.microsoft.com/.NetConfiguration/v2.0#linkedConfiguration
helpviewer_keywords:
- configuration files [.NET Framework],linked configuration files
- <linkedConfiguration> element
- including configuration files
- linked configuration files
- linkedConfiguration Element
ms.assetid: 8eb34f3b-427e-4288-a7ff-c73f489deb45
ms.openlocfilehash: 14ee2275ecf690ab16ffaabd71fbbe7e1a4897bc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/06/2020
ms.locfileid: "74087964"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration>, element

Określa plik konfiguracji, który ma zostać uwzględniony.

[**\<configuration>**](configuration-element.md)\
&nbsp;&nbsp;[**\<assemblyBinding>**](assemblybinding-element-for-configuration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<linkedConfiguration>**

## <a name="syntax"></a>Składnia

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Tag**  | Atrybut wymagany.<br><br>Adres URL pliku konfiguracji, który ma zostać uwzględniony. Jedynym formatem obsługiwanym przez atrybut **href** jest `file://` . Obsługiwane są pliki lokalne i pliki UNC. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [**\<assemblyBinding>** Postaci](assemblybinding-element-for-configuration.md) | Określa zasady powiązań zestawów na poziomie konfiguracji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<linkedConfiguration>** Element upraszcza obsługę zestawów składników. Jeśli co najmniej jedna aplikacja korzysta z zestawu, który ma plik konfiguracji znajdujący się w dobrze znanej lokalizacji, pliki konfiguracyjne aplikacji korzystających z zestawu mogą używać **\<linkedConfiguration>** elementu do dołączenia pliku konfiguracji zestawu, a nie bezpośredniego uwzględnienia informacji o konfiguracji. Gdy zestaw składników jest serwisowany, aktualizacja wspólnego pliku konfiguracji zawiera zaktualizowane informacje o konfiguracji do wszystkich aplikacji, które korzystają z zestawu.

> [!NOTE]
> **\<linkedConfiguration>** Element nie jest obsługiwany w przypadku aplikacji z manifestami równoległymi systemu Windows.

Zastosowanie połączonych plików konfiguracji podlega następującym zasadom:

- Ustawienia w zawartych plikach konfiguracji mają wpływ tylko na zasady powiązań modułu ładującego i są używane tylko przez moduł ładujący. Dołączone pliki konfiguracji mogą mieć ustawienia inne niż zasady powiązań, ale te ustawienia nie mają żadnego efektu.

- Jedynym formatem obsługiwanym przez `href` atrybut jest `file://` . Obsługiwane są pliki lokalne i pliki UNC.

- Brak ograniczeń liczby połączonych konfiguracji na plik konfiguracyjny.

- Wszystkie połączone pliki konfiguracji są scalane w celu utworzenia jednego pliku, podobnie jak zachowanie `#include` dyrektywy w C/C++.

- **\<linkedConfiguration>** Element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowany w *pliku Machine. config*.

- Odwołania cykliczne są wykrywane i kończone. Oznacza to, że jeśli **\<linkedConfiguration>** elementy serii plików konfiguracji tworzą pętlę, pętla zostanie wykryta i zatrzymana.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak dołączyć plik konfiguracji z lokalnego dysku twardego:

```xml
<configuration>
  <assemblyBinding xmlns="urn:schemas-microsoft-com:asm.v1">
    <linkedConfiguration href="file://c:\Program Files\Contoso\sharedConfig.xml"/>
  </assemblyBinding>
</configuration>
```

## <a name="see-also"></a>Zobacz także

- [**\<assemblyBinding>** Postaci](assemblybinding-element-for-configuration.md)
- [Schemat pliku konfiguracji dla .NET Framework](index.md)
