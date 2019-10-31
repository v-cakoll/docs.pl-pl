---
title: Co jest przestarzałe w bibliotece klas .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 4de441ff55c3728f43742d6e467deeb47f400507
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140597"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>Co jest przestarzałe w bibliotece klas .NET Framework

.NET Framework zmiany w czasie. Każda nowa wersja dodaje nowe typy i składowe typu, które udostępniają nowe funkcje. Istniejące typy i ich członkowie również zmieniają się wraz z upływem czasu. Na przykład niektóre typy stają się mniej ważne, ponieważ technologia, którą obsługują, jest zastępowana nową technologią, a niektóre metody są zastępowane nowszymi metodami, które są bardziej wygodne lub bardziej funkcjonalne.

.NET Framework i środowisko uruchomieniowe języka wspólnego dążą do obsługi zgodności z poprzednimi wersjami (dzięki czemu aplikacje, które zostały opracowane przy użyciu jednej wersji .NET Framework do uruchomienia w następnej wersji .NET Framework). Utrudnia to po prostu usunięcie typu lub elementu członkowskiego typu. Zamiast tego .NET Framework wskazuje, że typ lub element członkowski typu nie powinny być już używane przez oznaczenie go jako przestarzałe lub przestarzałe. Wycofanie typu lub elementu członkowskiego polega na oznaczeniu go w taki sposób, aby deweloperzy wiedzieli, że przestanie odpowiadać na usunięcie. Jednak istniejący kod, który używa typu lub elementu członkowskiego, kontynuuje działanie w nowej wersji .NET Framework.

> [!NOTE]
> Warunki *przestarzałe* i *przestarzałe* mają takie samo znaczenie, gdy są stosowane do typów i członków .NET Framework.

## <a name="the-obsoleteattribute-attribute"></a>Atrybut ObsoleteAttribute

.NET Framework wskazuje, że typ lub element członkowski typu jest przestarzały poprzez oznaczenie go atrybutem <xref:System.ObsoleteAttribute>. Zastosowanie atrybutu do typu lub elementu członkowskiego wskazuje, że typ lub członek zostanie usunięty w przyszłych wersjach .NET Framework bez dzielenia skompilowanego kodu, który używa tego elementu członkowskiego.

Oprócz wskazuje, że typ lub element członkowski typu są przestarzałe, <xref:System.ObsoleteAttribute> definiuje, jak kompilator obsługuje kod źródłowy, który zawiera ten typ lub element członkowski. Kompilator może skompilować kod, ale emituje komunikat ostrzegawczy lub może traktować użycie typu lub elementu członkowskiego jako błędu. W pierwszym przypadku kod można skompilować pomyślnie, ale komunikat ostrzegawczy wskazuje, że typ lub element członkowski jest przestarzały. W drugim przypadku kompilacja kończy się niepowodzeniem.

Nawet jeśli kompilacja generuje błąd zamiast komunikatu ostrzegawczego, <xref:System.ObsoleteAttribute> nie ma wpływu na zachowanie w czasie wykonywania. Oznacza to, że aplikacje używające typu lub elementu członkowskiego, które zostały pomyślnie skompilowane, będą zawsze uruchamiane pomyślnie. Tylko próba ponownego skompilowania aplikacji używającej typu lub składowej kończy się niepowodzeniem.

## <a name="how-to-handle-obsolete-types-and-members"></a>Jak obsłużyć przestarzałe typy i składowe

Po uaktualnieniu i ponownym skompilowaniu istniejącego kodu przy użyciu przestarzałego typu lub elementu członkowskiego, który generuje ostrzeżenie kompilatora w aplikacji, jest doskonale akceptowalna. Należy jednak przejrzeć komunikat ostrzegawczy kompilatora, aby określić, czy należy zmienić kod aplikacji. Jeśli komunikat nie wskazuje odpowiedniej alternatywy, należy wykonać jedną z następujących czynności:

- Zmień kod, usuwając użycie typu lub elementu członkowskiego, jeśli jest to możliwe.

     —lub—

- Zapoznaj się z dokumentacją tego obszaru technologii, aby określić, jak odpowiedzieć na wycofanie.

Możesz zrezygnować z ponownego kompilowania istniejącego kodu do nowszej wersji .NET Framework. Zamiast tego można określić wersję .NET Framework, do której zostanie uruchomiony istniejący skompilowany kod. Załóżmy na przykład, że masz aplikację o nazwie APP1. exe skompilowaną pod kątem .NET Framework 3,5, ale chcesz, aby aplikacja działała względem .NET Framework 4,5. Wymaga to wykonania następujących czynności:

1. Utwórz plik konfiguracji dla głównego pliku wykonywalnego i nadaj mu nazwę *nazwa_aplikacji*. exe. config, gdzie *nazwa_aplikacji* jest nazwą pliku wykonywalnego aplikacji. W przypadku aplikacji o nazwie APP1. exe w naszym przykładzie należy utworzyć plik konfiguracji o nazwie APP1. exe. config.

2. Dodaj następujący plik do pliku konfiguracji.

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

Poniższa tabela zawiera listę wartości ciągów, które można przypisać do atrybutu `version`, aby określić docelową wersję .NET Framework:

|Wersja programu .NET Framework|ciąg `version`|
|-|-|
|4,8|wersja|
|4,7 (w tym 4.7.1 i 4.7.2)|wersja|
|4,6 (w tym 4.6.1 i 4.6.2)|wersja|
|4,5 (w tym 4.5.1 i 4.5.2)|wersja|
|4|wersja|
|3.5|2\.0.50727 v|
|2.0|2\.0.50727 v|
|1.1|1\.1.4322 v|
|1.0|1\.0.3705 v|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a>Przestarzałe listy dla .NET Framework 4,5 i nowszych wersji

- [Przestarzałe typy](obsolete-types.md)
- [Przestarzałe elementy członkowskie](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a>Przestarzałe listy dla poprzednich wersji

- [Przestarzałe typy w .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))

- [Przestarzałe składowe w .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))

- [Nieaktualna lista .NET Framework 3,5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))

- [Nieaktualna lista .NET Framework 2,0](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>Zobacz także

- [\<element > supportedRuntime](../configure-apps/file-schema/startup/supportedruntime-element.md)
