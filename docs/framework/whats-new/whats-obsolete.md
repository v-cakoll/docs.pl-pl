---
title: Co jest przestarzałe w platformie .NET Framework
ms.custom: updateeachrelease
ms.date: 04/02/2019
helpviewer_keywords:
- obsolete [.NET Framework]
- what's obsolete [.NET Framework]
- deprecated [.NET Framework]
ms.assetid: d356a43a-73df-4ae2-a457-b9628074c7cd
ms.openlocfilehash: 7cfebfde859a95495e9d2d5e42bd034ad5d55e61
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79143138"
---
# <a name="whats-obsolete-in-the-net-framework-class-library"></a>Co jest przestarzałe w bibliotece klas programu .NET Framework

.NET zmienia się wraz z czasem. Każda nowa wersja dodaje nowe typy i elementy członkowskie typu, które zapewniają nowe funkcje. Istniejące typy i ich członkowie również zmieniają się wraz z czasem. Na przykład niektóre typy stają się mniej ważne, ponieważ technologia, którą obsługują, jest zastępowana przez nową technologię, a niektóre metody są zastępowane nowszymi metodami, które są w jakiś sposób lepsze.

.NET Framework i środowiska wykonawczego języka wspólnego dążyć do obsługi zgodności z powrotem (dzięki czemu aplikacje, które zostały opracowane z jedną wersją programu .NET Framework do uruchomienia w następnej wersji programu .NET Framework). To sprawia, że trudno po prostu usunąć typ lub element członkowski typu. Zamiast tego .NET wskazuje, że typ lub element członkowski typu nie powinny być już używane przez oznaczenie go jako przestarzałe lub przestarzałe. Przestarzałe typu lub elementu członkowskiego obejmuje oznaczenie go tak, że deweloperzy są świadomi, że zniknie i mają czas, aby odpowiedzieć na jego usunięcie. Jednak istniejący kod, który używa typu lub elementu członkowskiego nadal działa w nowej wersji platformy .NET.

> [!NOTE]
> Terminy *przestarzałe* i *przestarzałe* mają takie samo znaczenie, gdy są stosowane do typów .NET i elementów członkowskich.

## <a name="the-obsoleteattribute-attribute"></a>Atrybut ObsoleteAttribute

.NET Framework wskazuje, że element członkowski typu lub <xref:System.ObsoleteAttribute> typu jest przestarzały, oznaczając go atrybutem. Zastosowanie atrybutu do typu lub elementu członkowskiego wskazuje, że typ lub element członkowski zostaną usunięte w niektórych przyszłych wersjach programu .NET Framework bez przerywania skompilowany kod, który używa tego elementu członkowskiego.

Oprócz wskazania, że typ lub element członkowski typu jest przestarzały, definiuje sposób, <xref:System.ObsoleteAttribute> w jaki kompilator obsługuje kod źródłowy, który zawiera ten typ lub element członkowski. Kompilator może skompilować kod, ale emitować komunikat ostrzegawczy lub może traktować użycie typu lub elementu członkowskiego jako błąd. W pierwszym przypadku kod można pomyślnie skompilować, ale komunikat ostrzegawczy wskazuje, że typ lub element członkowski jest przestarzały. W drugim przypadku kompilacja kończy się niepowodzeniem.

Nawet jeśli kompilacja generuje błąd zamiast komunikatu <xref:System.ObsoleteAttribute> ostrzegawczego, nie wpływa na zachowanie w czasie wykonywania. Oznacza to, że aplikacje, które używają typu lub elementu członkowskiego i które zostały pomyślnie skompilowane zawsze będzie działać pomyślnie. Tylko próba ponownej kompilacji aplikacji, która używa typu lub elementu członkowskiego kończy się niepowodzeniem.

## <a name="how-to-handle-obsolete-types-and-members"></a>Jak obsługiwać przestarzałe typy i elementy członkowskie

Podczas uaktualniania i ponownego kompilowania istniejącego kodu, przy użyciu przestarzałego typu lub elementu członkowskiego, który generuje ostrzeżenie kompilatora w aplikacji jest całkowicie dopuszczalne. Jednak należy przejrzeć komunikat ostrzegawczy kompilatora, aby ustalić, czy należy zmienić kod aplikacji. Jeśli komunikat nie wskazuje odpowiedniej alternatywy, należy wykonać jedną z następujących czynności:

- Zmień kod, usuwając użycie typu lub elementu członkowskiego, jeśli to możliwe.

     — lub —

- Przejrzyj dokumentację dla tego obszaru technologii, aby ustalić, jak reagować na wycofanie.

Można nie ponownie skompilować istniejącego kodu względem nowszej wersji programu .NET Framework. Zamiast tego można określić wersję programu .NET Framework, z którym uruchamia się istniejący skompilowany kod. Załóżmy na przykład, że masz aplikację o nazwie app1.exe, która została skompilowana z programem .NET Framework 3.5, ale chcesz, aby aplikacja była uruchamiana względem programu .NET Framework 4.5. Wymaga to następujących kroków:

1. Utwórz plik konfiguracyjny dla głównego pliku wykonywalnego i nazwij go *appName*.exe.config, gdzie *appName* jest nazwą pliku wykonywalnego aplikacji. Dla aplikacji o nazwie *app1.exe* w naszym przykładzie należy utworzyć plik konfiguracyjny o nazwie *app1.exe.config*.

2. Dodaj następujące elementy do pliku konfiguracyjnego.

    ```xml
    <configuration>
       <startup>
          <supportedRuntime version="v4.0" />
       </startup>
    </configuration>
    ```

Aby kierować na określoną wersję programu .NET Framework, `version` przypisz do atrybutu jedną z następujących wartości ciągu:

|Wersja programu .NET Framework|`version`Ciąg|
|-|-|
|4.8|wersja 4.0|
|4,7 (w tym 4,7,1 i 4,7,2)|wersja 4.0|
|4,6 (w tym 4,6,1 i 4,6,2)|wersja 4.0|
|4,5 (w tym 4,5,1 i 4,5,2)|wersja 4.0|
|4|wersja 4.0|
|3,5|wersja 2.0.50727|
|2.0|wersja 2.0.50727|
|1.1|wersja 1.1.4322|
|1.0|wersja 1.0.3705|

## <a name="obsolete-apis-for-net-framework-45-and-later-versions"></a>Przestarzałe interfejsy API dla platformy .NET Framework 4.5 i nowszych wersji

- [Przestarzałe typy](obsolete-types.md)
- [Przestarzali członkowie](obsolete-members.md)

## <a name="obsolete-apis-for-previous-versions"></a>Przestarzałe interfejsy API dla poprzednich wersji

- [Przestarzałe typy w platformie .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee461503(v=vs.100))
- [Przestarzałe elementy członkowskie w ramach .NET Framework 4](https://docs.microsoft.com/previous-versions/dotnet/netframework-4.0/ee471421(v=vs.100))
- [.NET Framework 3.5 Przestarzała lista](https://docs.microsoft.com/previous-versions/cc835481(v=msdn.10))
- [.NET Framework 2.0 Przestarzała lista](https://docs.microsoft.com/previous-versions/aa497286(v=msdn.10))

## <a name="see-also"></a>Zobacz też

- [\<supportedRuntime> Element](../configure-apps/file-schema/startup/supportedruntime-element.md)
