---
title: What's Obsolete w bibliotece klas programu .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 81ca3721d33688d320ee553e32202617fe01aa5e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61914215"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>Co to jest przestarzała w bibliotece klas programu .NET Framework

.NET Framework zmienia się wraz z upływem czasu. Każda nowa wersja dodaje nowe typy i składowe typu, które zapewniają nowe funkcje. Istniejące typy i składowe są również zmienić wraz z upływem czasu. Na przykład niektóre typy stać się mniej ważne technologii, które obsługują zostaje zastąpiona przez nową technologię, a niektóre metody są zastępowane przez nowszą metody, które są bardziej wygodne lub zaawansowanych funkcji.

.NET Framework i środowiska uruchomieniowego języka wspólnego Dokładamy wszelkich starań obsługiwać zgodność z poprzednimi wersjami (dzięki czemu aplikacje, które zostały opracowane z jednej wersji programu .NET Framework do uruchamiania w następnej wersji programu .NET Framework). Utrudnia to po prostu usunąć typu lub składowej typu. Zamiast tego programu .NET Framework wskazuje, że typu lub składowej typu powinna nie jest już używane, oznaczając je jako nieaktualne lub przestarzały. Wycofano typu lub elementu członkowskiego obejmuje, oznaczając je, tak aby deweloperzy mają świadomość spowoduje pozbycie i masz czasu na odpowiadanie na jego usunięcie. Jednak istniejący kod, który używa typu lub elementu członkowskiego kontynuuje działanie w nowej wersji programu .NET Framework.

> [!NOTE]
> Warunki *przestarzałe* i *przestarzałe* mają takie samo znaczenie, gdy jest stosowany do typów i członków programu .NET Framework.

## <a name="the-obsoleteattribute-attribute"></a>Atrybut ObsoleteAttribute

.NET Framework wskazuje, że dany typ lub członek typu jest przestarzałe, oznaczając je za pomocą <xref:System.ObsoleteAttribute> atrybutu. Stosowanie atrybutu do typu lub elementu członkowskiego wskazuje, że typ lub element członkowski zostanie usunięta w niektórych przyszłych wersjach programu .NET Framework bez kod skompilowany podziału, który używa tego członka.

Oprócz wskazujący, że typ lub członek typu jest przestarzały, <xref:System.ObsoleteAttribute> definiuje, jak kompilator obsługuje kod źródłowy, który zawiera tego typu lub elementu członkowskiego. Kompilator może skompilować kod, ale emitują komunikat ostrzegawczy lub użycie typu lub elementu członkowskiego go traktować jako błąd. W pierwszym przypadku pomyślnie skompilować kod, ale komunikat ostrzegawczy wskazuje, że typ lub element członkowski jest przestarzały. W drugim przypadku kompilacja kończy się niepowodzeniem.

Nawet wtedy, gdy kompilacja generuje błąd zamiast komunikat ostrzegawczy <xref:System.ObsoleteAttribute> nie ma wpływu na zachowanie w czasie wykonywania. Oznacza to, że aplikacje, które korzystają z typu lub elementu członkowskiego i która została wykonana pomyślnie zawsze będzie uruchomione pomyślnie. Tylko próba ponownego kompilowania aplikacji korzystającej z typu lub elementu członkowskiego nie powiedzie się.

## <a name="how-to-handle-obsolete-types-and-members"></a>Jak obsługiwać przestarzałych typów i członków

Podczas uaktualniania i ponownie skompilować istniejący kod, za pomocą przestarzałego typu lub elementu członkowskiego, który generuje ostrzeżenie kompilatora w aplikacji jest idealnie dopuszczalne. Jednakże należy zapoznać się z komunikatem ostrzegawczym kompilatora, aby ustalić, czy należy zmienić kod aplikacji. Jeśli komunikat nie wskazuje odpowiedniego alternatywnego, powinny wykonaj jedną z następujących czynności:

- Zmień swój kod, usuwając użycie typu lub elementu członkowskiego, jeśli jest to możliwe.

     —lub—

- Przejrzyj dokumentację dla tego obszaru technologii określić, jak reagować na amortyzacja.

Może nie chcesz ponownie skompilować istniejący kod w nowszej wersji programu .NET Framework. Zamiast tego można określić wersji programu .NET Framework, względem którego istniejącą skompilowany kod działa. Na przykład załóżmy, że masz aplikację o nazwie app1.exe, który został skompilowany [!INCLUDE[net_v35_short](../../../includes/net-v35-short-md.md)], ale chcesz, aby uruchamiać aplikację [!INCLUDE[net_v45](../../../includes/net-v45-md.md)]. Wymagane jest wykonanie następujących kroków:

1. Utwórz plik konfiguracji dla użytkownika głównego pliku wykonywalnego i nadaj mu nazwę *appName*. exe.config, gdzie *appName* jest nazwą pliku wykonywalnego aplikacji. Dla aplikacji o nazwie app1.exe w naszym przykładzie należy utworzyć plik konfiguracji o nazwie app1.exe.config.

2. Dodaj następujący element do pliku konfiguracji.

    ```xml
    <configuration>
       <startup> 
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

W poniższej tabeli wymieniono wartości ciągów, które można przypisać do `version` atrybut pod kątem określonej wersji programu .NET Framework:

|Wersja programu .NET Framework|`version` ciąg|
|-|-|
|4.8|w wersji 4.0|
|4.7 (w tym 4.7.1 i 4.7.2)|w wersji 4.0|
|4.6 (w tym 4.6.1 i 4.6.2)|w wersji 4.0|
|4.5 (w tym 4.5.1 i 4.5.2)|w wersji 4.0|
|4|w wersji 4.0|
|3.5|v2.0.50727|
|2.0|v2.0.50727|
|1.1|v1.1.4322|
|1.0|v1.0.3705|

## <a name="obsolete-lists-for-the-net-framework-45-and-later-versions"></a>Przestarzałe listy dla .NET Framework 4.5 lub nowszy

- [Przestarzałe typy](obsolete-types.md)
- [Przestarzałe elementy członkowskie](obsolete-members.md)

## <a name="obsolete-lists-for-previous-versions"></a>Przestarzałe list dla wcześniejszych wersji

- [Przestarzałe typy w programie .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))

- [Przestarzali członkowie w .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))

- [Lista przestarzałe programu .NET framework 3.5](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))

- [.NET framework 2.0 przestarzałe listy](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>Zobacz także

- [\<supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md)