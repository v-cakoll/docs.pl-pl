---
title: Technologie .NET Framework niedostępne w platformie .NET Core
titleSuffix: ''
description: Dowiedz się więcej o technologiach .NET Framework, które są niedostępne w platformie .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: bd2488de653ecdfed261100b4c9019bea58fcab3
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "77092944"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologie .NET Framework niedostępne w platformie .NET Core

Kilka technologii dostępnych dla bibliotek programu .NET Framework nie jest dostępnych do użycia z platformą .NET Core, takimi jak AppDomains, Remoting, Code Access Security (CAS), Security Transparency i System.EnterpriseServices. Jeśli biblioteki opierają się na jednej lub więcej z tych technologii, należy wziąć pod uwagę alternatywne podejścia opisane poniżej. Aby uzyskać więcej informacji na temat zgodności interfejsu API, zobacz [.NET Core przełomowe zmiany](../compatibility/breaking-changes.md).

Tylko dlatego, że interfejs API lub technologia nie jest obecnie zaimplementowana nie oznacza, że jest celowo nieobsługiwane. Przeszukaj repozytoria GitHub dla .NET Core, aby sprawdzić, czy napotkany problem jest według projektu. Jeśli nie znajdziesz takiego wskaźnika, zgłać problem w [repozytorium dotnet/runtime,](https://github.com/dotnet/runtime/issues) aby poprosić o podanie określonych interfejsów API i technologii. Problemy, które są przenoszenie żądań są oznaczone etykietą [port-to-core.](https://github.com/dotnet/runtime/labels/port-to-core)

## <a name="appdomains"></a>Domeny aplikacji

Domeny aplikacji (AppDomains) izolują aplikacje od siebie nawzajem. AppDomains wymagają obsługi w czasie wykonywania i są zazwyczaj dość drogie. Tworzenie dodatkowych domen aplikacji nie jest obsługiwane i nie ma planów, aby dodać tę funkcję w przyszłości. W przypadku izolacji kodu należy użyć oddzielnych procesów lub kontenerów jako alternatywy. Aby dynamicznie ładować zespoły, należy użyć <xref:System.Runtime.Loader.AssemblyLoadContext> klasy.

Aby ułatwić migrację kodu z platformy .NET Framework, <xref:System.AppDomain> program .NET Core udostępnia część powierzchni interfejsu API. Niektóre interfejsy API działają normalnie <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>(na przykład), niektórzy <xref:System.AppDomain.SetCachePath%2A>członkowie nic nie <xref:System.PlatformNotSupportedException> robią (na <xref:System.AppDomain.CreateDomain%2A>przykład), a niektóre z nich wyrzucają (na przykład). Sprawdź typy używane względem [ `System.AppDomain` źródła odwołania](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) w [repozytorium GitHub dotnet/runtime](https://github.com/dotnet/runtime). Upewnij się, że wybierz gałąź, która pasuje do zaimplementowanej wersji.

## <a name="remoting"></a>Usług zdalnych

.NET Komunikacji zdalnej został zidentyfikowany jako problematyczne architektury. Jest on używany do komunikacji między AppDomain, który nie jest już obsługiwany. Ponadto komunikacji zdalnej wymaga obsługi w czasie wykonywania, która jest kosztowna w utrzymaniu. Z tych powodów usługi .NET Komunikacji zdalnej nie jest obsługiwana w usłudze .NET Core i nie planujemy dodawania obsługi w przyszłości.

W przypadku komunikacji między procesami należy wziąć pod uwagę mechanizmy komunikacji międzyprocesowej (IPC) jako alternatywę dla komunikacji zdalnej, takie jak <xref:System.IO.Pipes> klasa lub <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> klasa.

Na różnych komputerach użyj rozwiązania opartego na sieci jako alternatywy. Najlepiej użyć protokołu zwykłego tekstu o niskim poziomie narzutów, takiego jak HTTP. [Kestrel web server](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), serwer www używany przez ASP.NET Core, jest opcją tutaj. Należy również <xref:System.Net.Sockets> rozważyć użycie dla scenariuszy opartych na sieci, między komputerami. Aby uzyskać więcej opcji, zobacz [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)

Piaskowcy, który opiera się na czasie wykonywania lub ramach, aby ograniczyć, które zasoby zarządzanej aplikacji lub biblioteki używa lub uruchamia, [nie jest obsługiwana w .NET Framework](../../framework/misc/code-access-security.md) i dlatego nie jest również obsługiwana w .NET Core. Istnieje zbyt wiele przypadków w .NET Framework i w czasie wykonywania, gdzie występuje podniesienie uprawnień, aby kontynuować traktowanie cas jako granicę zabezpieczeń. Ponadto cas sprawia, że implementacja bardziej skomplikowane i często ma wpływ na poprawność wydajności dla aplikacji, które nie zamierzają go używać.

Użyj granic zabezpieczeń dostarczonych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników, do uruchamiania procesów z minimalnym zestawem uprawnień.

## <a name="security-transparency"></a>Przejrzystość zabezpieczeń

Podobnie jak w przypadku cas, przezroczystość zabezpieczeń oddziela kod w schowku piaskowym od kodu krytycznego zabezpieczeń w sposób deklaratywny, ale nie jest [już obsługiwany jako granica zabezpieczeń.](../../framework/misc/security-transparent-code.md) Ta funkcja jest intensywnie używana przez Silverlight.

Użyj granic zabezpieczeń dostarczonych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników, do uruchamiania procesów z najmniejszym zestawem uprawnień.

## <a name="systementerpriseservices"></a>System.enterpriseservices

System.EnterpriseServices (COM+) nie jest obsługiwany przez .NET Core.

## <a name="see-also"></a>Zobacz też

- [Omówienie przenoszenia z platformy .NET Framework do programu .NET Core](../porting/index.md)
