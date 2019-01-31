---
title: <useLegacyJit>, element
ms.date: 04/26/2017
ms.assetid: c2cf97f0-9262-4f1f-a754-5568b51110ad
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a467599084f01b1a48c95c5e25fb1f869156dffa
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/30/2019
ms.locfileid: "55278762"
---
# <a name="uselegacyjit-element"></a>\<useLegacyJit> Element

Określa, czy środowisko uruchomieniowe języka wspólnego używa starszej wersji 64-bitowy kompilator JIT dla kompilacji just in time.  
  
\<Konfiguracja >  
\<runtime>  
\<useLegacyJit>
  
## <a name="syntax"></a>Składnia  
  
```xml
<useLegacyJit enabled=0|1 />
```

Nazwa elementu `useLegacyJit` jest uwzględniana wielkość liter.
  
## <a name="attributes-and-elements"></a>Atrybuty i elementy

W poniższych sekcjach opisano atrybuty, elementy podrzędne i elementy nadrzędne.  
  
### <a name="attributes"></a>Atrybuty  
  
| Atrybut | Opis                                                                                   |  
| --------- | --------------------------------------------------------------------------------------------- |  
| `enabled` | Atrybut wymagany.<br><br>Określa, czy środowisko wykonawcze używa starszej wersji 64-bitowego kompilatora JIT. |  
  
### <a name="enabled-attribute"></a>Atrybut włączony  
  
| Wartość | Opis                                                                                                         |  
| ----- | ------------------------------------------------------------------------------------------------------------------- |  
| 0     | Środowisko uruchomieniowe języka wspólnego używa nowego 64-bitowy kompilator JIT zawarte w .NET Framework 4.6 lub nowszy. |  
| 1     | Środowisko uruchomieniowe języka wspólnego używa starszej 64-bitowego kompilatora JIT.                                                     |  
  
### <a name="child-elements"></a>Elementy podrzędne

Brak
  
### <a name="parent-elements"></a>Elementy nadrzędne  
  
| Element         | Opis                                                                                                       |  
| --------------- | ----------------------------------------------------------------------------------------------------------------- |  
| `configuration` | Element główny w każdym pliku konfiguracji używanym przez środowisko uruchomieniowe języka wspólnego i aplikacje programu .NET Framework. |  
| `runtime`       | Zawiera informacje dotyczące opcji inicjowania środowiska uruchomieniowego.                                                        |  
  
## <a name="remarks"></a>Uwagi  

Począwszy od programu .NET Framework 4.6, środowisko uruchomieniowe języka wspólnego nowy, 64-bitowego kompilatora dla kompilacji just in Time (JIT) domyślnie używa. W niektórych przypadkach może to spowodować różnice w zachowaniu w kodzie aplikacji, która została skompilowana JIT w poprzedniej wersji 64-bitowego kompilatora JIT. Ustawiając `enabled` atrybutu `<useLegacyJit>` elementu `1`, można wyłączyć nowego 64-bitowy kompilator JIT i zamiast tego Kompilowanie aplikacji za pomocą starszej wersji 64-bitowego kompilatora JIT.  
  
> [!NOTE]
> `<useLegacyJit>` Elementu dotyczy tylko kompilacja JIT w 64-bitowych. Kompilacja z 32-bitowy kompilator JIT pozostaje bez zmian.  
  
Zamiast korzystać z ustawień pliku konfiguracji, należy włączyć starszej wersji 64-bitowy kompilator JIT, które na dwa inne sposoby:  
  
- Ustawienie zmiennej środowiskowej

  Ustaw `COMPLUS_useLegacyJit` zmiennej środowiskowej, aby albo `0` (Użyj nowego 64-bitowy kompilator JIT) lub `1` (Użyj starszych 64-bitowy kompilator JIT):
  
  ```  
  COMPLUS_useLegacyJit=0|1  
  ```  
  
  Zmienna środowiskowa została *zakresu globalnego*, co oznacza, że ma to wpływ na wszystkie aplikacje są uruchamiane na maszynie. Jeśli ustawiona, jego może zostać przesłonięta przez ustawienie pliku konfiguracji aplikacji. Zmienna środowiskowa nie jest rozróżniana wielkość liter.
  
- Dodawanie klucza rejestru

  Włącz starsze 64-bitowy kompilator JIT, dodając `REG_DWORD` wartość albo `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` lub `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza w rejestrze. Wartość o nazwie `useLegacyJit`. Jeśli wartość wynosi 0, jest używany nowy kompilator. Jeśli wartość wynosi 1, starszego 64-bitowy kompilator JIT jest włączona. Nazwa wartości rejestru nie jest rozróżniana wielkość liter.
  
  Dodaj wartość do `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchomione na komputerze. Dodaj wartość do `HKEY_CURRENT_USER\SOFTWARE\Microsoft\.NETFramework` klucza ma wpływ na wszystkie aplikacje uruchomione przez bieżącego użytkownika. Jeśli maszyna jest skonfigurowana z wieloma kontami użytkowników, tylko aplikacje uruchomione przez bieżącego użytkownika jest narażony, chyba, że wartość jest dodawana do kluczy rejestru, jak również do innych użytkowników. Dodawanie `<useLegacyJit>` element do pliku konfiguracji zastępuje ustawienia rejestru, jeśli są one obecne.  
  
## <a name="example"></a>Przykład  

Następujący plik konfiguracji powoduje wyłączenie kompilacji za pomocą nowego 64-bitowy kompilator JIT i zamiast tego używa starszej wersji 64-bitowego kompilatora JIT.  
  
```xml  
<?xml version ="1.0"?>  
<configuration>  
  <runtime>  
    <useLegacyJit enabled="1" />  
  </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Zobacz także

- [\<środowisko uruchomieniowe > Element](../../../../../docs/framework/configure-apps/file-schema/runtime/runtime-element.md)
- [\<Konfiguracja > Element](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)
- [Środki zaradcze: Nowy kompilator JIT 64-bitowych](../../../../../docs/framework/migration-guide/mitigation-new-64-bit-jit-compiler.md)
