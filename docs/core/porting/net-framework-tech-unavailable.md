---
title: Technologie .NET Framework niedostępne w programie .NET Core
titleSuffix: ''
description: Informacje na temat technologii .NET Framework, które są niedostępne w programie .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: b75d946b9436b1075a068494b941fbdea5970e42
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795602"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologie .NET Framework niedostępne w programie .NET Core

Niektóre technologie dostępne dla bibliotek .NET Framework nie są dostępne do użycia z platformą .NET Core, takich jak AppDomains, komunikacja zdalna, zabezpieczenia dostępu kodu (CAS), przezroczystość zabezpieczeń i system. EnterpriseServices. Jeśli biblioteki są zależne od co najmniej jednej z tych technologii, weź pod uwagę alternatywne podejścia opisane poniżej. Aby uzyskać więcej informacji na temat zgodności interfejsów API, zobacz [podstawowe zmiany w programie .NET Core](../compatibility/breaking-changes.md).

Tylko ponieważ interfejs API lub technologia nie jest obecnie zaimplementowana, nie oznacza to, że jest celowo nieobsługiwana. Przeszukaj repozytoria GitHub dla platformy .NET Core, aby sprawdzić, czy konkretny problem występuje w drodze projektu. Jeśli nie znajdziesz takiego wskaźnika, zgłoś problem w [repozytorium dotnet/Runtime](https://github.com/dotnet/runtime/issues) , aby uzyskać szczegółowe informacje o interfejsach API i technologiach.

## <a name="appdomains"></a>Domen aplikacji

Domeny aplikacji (AppDomains) izolują aplikacje od siebie. Domeny aplikacji wymagają obsługi środowiska uruchomieniowego i są generalnie kosztowne. Tworzenie dodatkowych domen aplikacji nie jest obsługiwane i nie ma żadnych planów, aby dodać tę możliwość w przyszłości. W przypadku izolacji kodu Użyj oddzielnych procesów lub kontenerów jako alternatywy. Aby dynamicznie ładować zestawy, użyj <xref:System.Runtime.Loader.AssemblyLoadContext> klasy.

Aby ułatwić migrację kodu z .NET Framework, środowisko .NET Core uwidacznia część powierzchni <xref:System.AppDomain> interfejsu API. Niektóre z interfejsów API działają normalnie <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>(na przykład), niektórzy członkowie nie wykonują żadnych operacji (na <xref:System.AppDomain.SetCachePath%2A>przykład), a niektóre z nich <xref:System.PlatformNotSupportedException> zgłaszają (na <xref:System.AppDomain.CreateDomain%2A>przykład). Sprawdź typy, które są używane w odniesieniu do [ `System.AppDomain` źródła odwołania](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) w [repozytorium usługi GitHub/środowiska uruchomieniowego](https://github.com/dotnet/runtime). Upewnij się, że wybrano gałąź zgodną z zaimplementowaną wersją.

## <a name="remoting"></a>Komunikacji zdalnej

Komunikacja zdalna .NET została zidentyfikowana jako problematyczna architektura. Jest on używany do komunikacji między domenami, która nie jest już obsługiwana. Ponadto komunikacja zdalna wymaga obsługi środowiska uruchomieniowego, co jest kosztowne do utrzymania. Z tego względu komunikacja zdalna .NET nie jest obsługiwana w przypadku platformy .NET Core i nie planuje się jej dodawania w przyszłości.

W przypadku komunikacji między procesami należy wziąć pod uwagę mechanizmy komunikacji między procesami (IPC) jako alternatywę dla usług zdalnych <xref:System.IO.Pipes> , takich jak <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> Klasa lub Klasa.

Na wielu maszynach Użyj rozwiązania sieciowego jako alternatywy. Najlepiej użyć niskiego obciążenia protokołu zwykłego tekstu, takiego jak HTTP. Serwer [sieci Web Kestrel](/aspnet/core/fundamentals/servers/kestrel), serwer sieci Web używany przez ASP.NET Core, jest opcją w tym miejscu. Należy również rozważyć użycie <xref:System.Net.Sockets> w przypadku scenariuszy opartych na sieci i wielu maszynach. Aby uzyskać więcej opcji, zobacz [projekty programu .NET Open Source Developer projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)

W przypadku korzystania z trybu piaskownicy, który polega na środowisku uruchomieniowym lub środowisku, aby ograniczyć zasoby, których zarządzana aplikacja lub biblioteka jest uruchomiona, [nie jest obsługiwane w .NET Framework](../../framework/misc/code-access-security.md) i dlatego nie jest również obsługiwane w programie .NET Core. W .NET Framework jest zbyt wiele przypadków i środowisko uruchomieniowe, w którym występuje podniesienie uprawnień, aby kontynuować traktowanie urzędów certyfikacji jako granic zabezpieczeń. Ponadto urzędy certyfikacji czynią implementację bardziej skomplikowaną i często mają prawidłowy wpływ na wydajność aplikacji, które nie będą używane.

Aby uruchamiać procesy z minimalnym zestawem uprawnień, należy używać granic zabezpieczeń zapewnianych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników.

## <a name="security-transparency"></a>Przejrzystość zabezpieczeń

Podobnie jak w przypadku urzędów certyfikacji, przezroczystość zabezpieczeń oddziela kod w trybie piaskownicy od krytycznego kodu zabezpieczeń w sposób deklaratywny, ale [nie jest już obsługiwany jako granica zabezpieczeń](../../framework/misc/security-transparent-code.md). Ta funkcja jest intensywnie używana przez program Silverlight.

Aby uruchamiać procesy z najmniej zestawem uprawnień, należy używać granic zabezpieczeń udostępnianych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników.

## <a name="systementerpriseservices"></a>System. EnterpriseServices

System. EnterpriseServices (COM+) nie jest obsługiwany przez platformę .NET Core.

## <a name="see-also"></a>Zobacz także

- [Przegląd portów z .NET Framework do platformy .NET Core](index.md)
