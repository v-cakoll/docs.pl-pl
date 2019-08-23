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
ms.openlocfilehash: a0b56ac66302f11c59c149197a84bb96691282a5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69921014"
---
# <a name="linkedconfiguration-element"></a>\<linkedConfiguration, element >

Określa plik konfiguracji, który ma zostać uwzględniony.

[ **\<> konfiguracji**](configuration-element.md)   
&nbsp;&nbsp;[ **\<> zestawubinding**](assemblybinding-element-for-configuration.md)   
&nbsp;&nbsp;&nbsp;&nbsp; **\<linkedConfiguration>**

## <a name="syntax"></a>Składnia

```xml
<linkedConfiguration href="URL of linked configuration file" />
```

## <a name="attribute"></a>Atrybut

|           | Opis |
| --------- | ----------- |
| **Tag**  | Atrybut wymagany.<br><br>Adres URL pliku konfiguracji, który ma zostać uwzględniony. Jedynym formatem obsługiwanym przez atrybut **href** jest `file://`. Obsługiwane są pliki lokalne i pliki UNC. |

## <a name="parent-element"></a>Element nadrzędny

|     | Opis |
| --- | ----------- |
| [assemblyBinding — element >  **\<** ](assemblybinding-element-for-configuration.md) | Określa zasady powiązań zestawów na poziomie konfiguracji. |

## <a name="child-elements"></a>Elementy podrzędne

Brak

## <a name="remarks"></a>Uwagi

**\<Linkedconfiguration — >** element upraszcza obsługę techniczną dla zestawów składników. Co najmniej jednej aplikacji, użycie zestawu, który zawiera plik konfiguracji znajdujących się w lokalizacji, dobrze znanego, pliki konfiguracji aplikacji, które używają zestawu można użyć **\<linkedconfiguration — >** element, aby uwzględnić plik konfiguracji zestawu, a nie bezpośrednio w tym informacje o konfiguracji. Gdy zestaw składników jest serwisowany, aktualizacja wspólnego pliku konfiguracji zawiera zaktualizowane informacje o konfiguracji do wszystkich aplikacji, które korzystają z zestawu.

> [!NOTE]
> **\<Linkedconfiguration — >** element nie jest obsługiwany w przypadku aplikacji o Windows side-by-side manifestów.

Zastosowanie połączonych plików konfiguracji podlega następującym zasadom:

- Ustawienia w zawartych plikach konfiguracji mają wpływ tylko na zasady powiązań modułu ładującego i są używane tylko przez moduł ładujący. Dołączone pliki konfiguracji mogą mieć ustawienia inne niż zasady powiązań, ale te ustawienia nie mają żadnego efektu.

- Jedynym formatem obsługiwanym przez `href` atrybut jest. `file://` Obsługiwane są pliki lokalne i pliki UNC.

- Brak ograniczeń liczby połączonych konfiguracji na plik konfiguracyjny.

- Wszystkie połączone pliki konfiguracji są scalane w celu utworzenia jednego pliku, podobnie jak w przypadku `#include` zachowania dyrektywy w językuC++C/.

- **\<Linkedconfiguration — >** element jest dozwolony tylko w plikach konfiguracji aplikacji; jest ignorowana w *Machine.config*.

- Odwołania cykliczne są wykrywane i kończone. Oznacza to jeśli **\<linkedconfiguration — >** elementy szeregu plików konfiguracyjnych tworzą pętli, pętla jest wykrywany i zatrzymane.

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

- [assemblyBinding — element >  **\<** ](assemblybinding-element-for-configuration.md)
- [Schemat pliku konfiguracji dla .NET Framework](index.md)
