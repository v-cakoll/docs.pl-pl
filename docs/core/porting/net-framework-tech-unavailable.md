---
title: Technologii .NET framework jest niedostępna na platformie .NET Core
description: Dowiedz się więcej o technologii .NET Framework, które nie są dostępne na platformie .NET Core
author: cartermp
ms.author: mairaw
ms.date: 12/7/2018
ms.openlocfilehash: 9d7860184806288dd0d5eb3b0447839d5e47c27f
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/16/2019
ms.locfileid: "58125476"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologii .NET framework jest niedostępna na platformie .NET Core

Technologie kilka, które są dostępne do bibliotek .NET Framework nie są dostępne do użytku z platformą .NET Core, takich jak domen aplikacji usług zdalnych, zabezpieczenia dostępu kodu (CAS) i przezroczystości zabezpieczeń. Jeśli bibliotek zależą od tego, co najmniej jeden z tych technologii, należy wziąć pod uwagę alternatywnych metod opisanych poniżej. Aby uzyskać więcej informacji na temat zgodności interfejsu API zespół CoreFX zachowuje [listy zmian zachowania/compat podziałów i przestarzałe/starszych interfejsów API](https://github.com/dotnet/corefx/wiki/ApiCompat) w witrynie GitHub.

Po prostu, ponieważ obecnie nie jest zaimplementowany interfejs API lub technologii nie oznacza, że celowo ma nieobsługiwany. Należy najpierw wyszukać repozytoriów GitHub dla programu .NET Core zobaczyć, jeśli konkretnego problemu wystąpi jest zgodnie z projektem, ale jeśli nie możesz znaleźć wskaźnik, zgłoś problem w [problemów w repozytorium dotnet/corefx](https://github.com/dotnet/corefx/issues) w witrynie GitHub, aby zadać dla określonych interfejsów API i technologii. [Eksportowanie żądań w kwestii](https://github.com/dotnet/corefx/labels/port-to-core) są oznaczone `port-to-core` etykiety.

## <a name="appdomains"></a>AppDomains

Domeny aplikacji (domen aplikacji) izolowania aplikacji od siebie nawzajem. Domen aplikacji, wymagana jest obsługa środowiska uruchomieniowego i zwykle są stosunkowo drogie. Tworzenie domen dodatkowych aplikacji nie jest obsługiwane... Nie planujemy dodać tę możliwość w przyszłości. Izolacja kodu, zaleca się oddzielnych procesach lub jako alternatywa przy użyciu kontenerów. Dynamiczne ładowanie zestawów, zaleca się nowym <xref:System.Runtime.Loader.AssemblyLoadContext> klasy.

Aby ułatwić migrację kodu z .NET Framework, .NET Core udostępnia część <xref:System.AppDomain> powierzchni interfejsu API. Niektóre z interfejsów API normalnego działania (na przykład <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>), niektóre elementy członkowskie nic nie rób (na przykład <xref:System.AppDomain.SetCachePath%2A>), i niektóre z nich throw <xref:System.PlatformNotSupportedException> (na przykład <xref:System.AppDomain.CreateDomain%2A>). Sprawdź typy używać względem [ `System.AppDomain` źródło odwołania](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) w [repozytorium GitHub dotnet/corefx](https://github.com/dotnet/corefx)i wybierz gałąź, który odpowiada używanej wersji zaimplementowano.

## <a name="remoting"></a>Komunikacja zdalna

Wywołaniem funkcji zdalnych .NET została zidentyfikowana jako architektura problematyczne. Jest używany do komunikacji między AppDomain nie jest już obsługiwana. Komunikacja zdalna wymaga również, obsługa środowiska uruchomieniowego, która jest kosztowna zachować. Z tego względu wywołaniem funkcji zdalnych .NET nie jest obsługiwana na platformie .NET Core i nie planujemy dodanie obsługi go w przyszłości.

Do komunikacji między procesami, należy wziąć pod uwagę mechanizmy komunikacji międzyprocesowej (IPC) jako alternatywę do komunikacji zdalnej, takich jak <xref:System.IO.Pipes> lub <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> klasy.

Na maszynach przy użyciu rozwiązania opartego na sieci jako alternatywa. Najlepiej używać protokołu małym obciążeniem zwykłego tekstu, takich jak HTTP. [Serwera sieci web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), serwer sieci web używane przez platformy ASP.NET Core jest opcją w tym miejscu. Ponadto należy wziąć pod uwagę przy użyciu <xref:System.Net.Sockets> do scenariuszy opartych na sieci, między komputerami. Aby uzyskać więcej opcji, zobacz [otwartych projektów źródła dla deweloperów platformy .NET: Komunikaty](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)

Tryb piaskownicy, która opiera się na środowisko uruchomieniowe lub platformę, by ograniczać zasoby aplikacji zarządzanej, czy biblioteka używa lub uruchamia, [nie jest obsługiwana w programie .NET Framework](~/docs/framework/misc/code-access-security.md) i dlatego też nie jest obsługiwana na platformie .NET Core. Istnieje za dużo przypadków w .NET Framework i środowiska uruchomieniowego realizowana podniesienie uprawnień, aby kontynuować, traktując urzędów certyfikacji pełnią funkcję granicy zabezpieczeń. Ponadto urzędów certyfikacji sprawia, że implementacja jest bardziej skomplikowane i często ma wpływ poprawność wydajności dla aplikacji, które nie będą z niego korzystać.

Użyj granic zabezpieczeń dostarczone przez system operacyjny, np. konta wirtualizacji, kontenerów lub użytkownika do uruchomionego procesu za pomocą minimalny zestaw uprawnień.

## <a name="security-transparency"></a>Przezroczystości zabezpieczeń

Podobnie jak urzędy certyfikacji, przezroczystości zabezpieczeń kodu w trybie piaskownicy są oddzielone od zabezpieczeń kod krytyczny w sposób deklaratywny, ale jest [nie są już obsługiwane jako granice zabezpieczeń](~/docs/framework/misc/security-transparent-code.md). Ta funkcja jest intensywnie używana przez program Silverlight. 

Użyj granic zabezpieczeń dostarczone przez system operacyjny, np. konta wirtualizacji, kontenerów lub użytkownika do uruchomionego procesu za pomocą najmniejszej zestaw uprawnień.

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
