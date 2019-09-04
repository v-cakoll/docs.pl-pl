---
title: <useLegacyJit>, element
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3b783a82b1ef964de308532ef544bbfab2397400
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252226"
---
# <a name="uselegacyjit-element"></a>\<useLegacyJit> Element

Określa, czy środowisko uruchomieniowe języka wspólnego korzysta ze starszego 64-bitowego kompilatora JIT dla kompilacji just in Time.  
  
[ **\<> konfiguracji**](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> środowiska uruchomieniowego**](runtime-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp; **\<useLegacyJit>**  
  
## <a name="syntax"></a>Składnia  
  
```xml
<useLegacyJit enabled=0|1 />
```

Nazwa `useLegacyJit` elementu uwzględnia wielkość liter.
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
| Atrybut | Opis                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Atrybut wymagany.<br><br>Określa, czy środowisko uruchomieniowe używa starszego 64-bitowego kompilatora JIT. |  
  
### <a name="enabled-attribute"></a>włączony atrybut  
  
| Wartość | Opis                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Środowisko uruchomieniowe języka wspólnego używa nowego kompilatora 64-bitowego JIT zawartego w .NET Framework 4,6 i nowszych wersjach. |  
| 1     | Środowisko uruchomieniowe języka wspólnego używa starszego 64-bitowego kompilatora JIT.                                                     |  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
| Element         | Opis                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |  
| `runtime`       | Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.                                                        |  
  
## <a name="remarks"></a>Uwagi  

Począwszy od .NET Framework 4,6, środowisko uruchomieniowe języka wspólnego używa nowego kompilatora 64-bitowego dla kompilacji just-in-Time (JIT) domyślnie. W niektórych przypadkach może to skutkować różnicą w zachowaniu kodu aplikacji, który był skompilowany przez poprzednią wersję 64-bitowego kompilatora JIT. Ustawiając `enabled` atrybut `<useLegacyJit>` elementu na`1`, można wyłączyć nowy kompilator 64-bitowy JIT, a zamiast tego skompilować aplikację przy użyciu starszego, 64-bitowego kompilatora JIT.  
  
> [!NOTE]
> `<useLegacyJit>` Element ma wpływ tylko na 64-bitową kompilację JIT. Kompilacja z 32-bitowym kompilatorem JIT nie ma żadnych zmian.  
  
Zamiast korzystać z ustawienia pliku konfiguracji, można włączyć starszy 64-bitowy kompilator JIT na dwa sposoby:  
  
- Ustawianie zmiennej środowiskowej

  Ustaw zmienną `0` `1` środowiskową na wartość (Użyj nowego kompilatora 64-bitowego JIT) lub (Użyj starszego, 64-bitowego kompilatora JIT): `COMPLUS_useLegacyJit`
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Zmienna środowiskowa ma *zakres globalny*, co oznacza, że ma wpływ na wszystkie aplikacje działające na komputerze. Jeśli ta opcja jest ustawiona, może być zastąpiona przez ustawienie pliku konfiguracji aplikacji. W nazwie zmiennej środowiskowej nie jest rozróżniana wielkość liter.
  
- Dodawanie klucza rejestru

  Można włączyć starszy kompilator 64-bitowy JIT, dodając `REG_DWORD` wartość do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` lub `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucz w rejestrze. Wartość jest nazywana `useLegacyJit`. Jeśli wartość jest równa 0, używany jest nowy kompilator. Jeśli wartość wynosi 1, jest włączony starszy 64-bitowy kompilator JIT. W nazwie wartości rejestru nie jest rozróżniana wielkość liter.
  
  Dodanie wartości do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchomione na komputerze. Dodanie wartości do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchamiane przez bieżącego użytkownika. Jeśli komputer jest skonfigurowany z wieloma kontami użytkowników, będzie to miało wpływ tylko na aplikacje uruchamiane przez bieżącego użytkownika, chyba że wartość zostanie dodana do kluczy rejestru dla innych użytkowników. `<useLegacyJit>` Dodanie elementu do pliku konfiguracji zastępuje ustawienia rejestru, jeśli są obecne.  
  
## <a name="example"></a>Przykład  

Następujący plik konfiguracji wyłącza kompilację z nowym 64-bitowym kompilatorem JIT, a zamiast tego używa starszego, 64-bitowego kompilatora JIT.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<Element > środowiska uruchomieniowego](runtime-element.md)
- [\<> elementu konfiguracji](../configuration-element.md)
- [Środki zaradcze Nowy 64-bitowy kompilator JIT](../../../migration-guide/mitigation-new-64-bit-jit-compiler.md)
