---
title: Technologie .NET Framework niedostępne w programie .NET Core
description: Informacje na temat technologii .NET Framework, które są niedostępne w programie .NET Core
author: cartermp
ms.author: mairaw
ms.date: 04/30/2019
ms.openlocfilehash: 87c3dd337ad44fd21b255afa7c03b528cd8a42ad
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660602"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologie .NET Framework niedostępne w programie .NET Core

Niektóre technologie dostępne dla bibliotek .NET Framework nie są dostępne do użycia z platformą .NET Core, takich jak AppDomains, komunikacja zdalna, zabezpieczenia dostępu kodu (CAS) i przezroczystość zabezpieczeń. Jeśli biblioteki są zależne od co najmniej jednej z tych technologii, weź pod uwagę alternatywne podejścia opisane poniżej. Aby uzyskać więcej informacji na temat zgodności interfejsu API, zespół CoreFX przechowuje [listę zmian zachowań/przerw w działaniu i przestarzałych/starszych interfejsów API](https://github.com/dotnet/corefx/wiki/ApiCompat) w serwisie GitHub.

Tylko ponieważ interfejs API lub technologia nie jest obecnie zaimplementowana, nie oznacza to, że jest celowo nieobsługiwana. Najpierw należy przeszukać repozytoria usługi GitHub dla platformy .NET Core, aby zobaczyć, czy konkretny problem występuje w drodze projektu, ale jeśli nie można znaleźć takiego wskaźnika, należy zgłosić problem z [repozytorium dotnet/corefx](https://github.com/dotnet/corefx/issues) w witrynie GitHub w celu poproszenia o określone interfejsy API i informacyjn. [Przenoszenie żądań w ramach problemów](https://github.com/dotnet/corefx/labels/port-to-core) jest oznaczone `port-to-core` etykietą.

## <a name="appdomains"></a>AppDomains

Domeny aplikacji (AppDomains) izolują aplikacje od siebie. Domeny aplikacji wymagają obsługi środowiska uruchomieniowego i są zwykle dość kosztowne. Tworzenie dodatkowych domen aplikacji nie jest obsługiwane. Nie planujemy dodawania tej funkcji w przyszłości. W przypadku izolacji kodu zaleca się oddzielne procesy lub używanie kontenerów jako alternatywy. W przypadku dynamicznego ładowania zestawów zalecamy nową <xref:System.Runtime.Loader.AssemblyLoadContext> klasę.

Aby ułatwić migrację kodu z .NET Framework, środowisko .NET Core uwidacznia część <xref:System.AppDomain> powierzchni interfejsu API. Niektóre z interfejsów API działają normalnie (na <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>przykład), niektórzy członkowie nie wykonują żadnych operacji (na <xref:System.AppDomain.SetCachePath%2A>przykład), <xref:System.PlatformNotSupportedException> a niektóre z nich zgłaszają (na <xref:System.AppDomain.CreateDomain%2A>przykład). Sprawdź typy, które są używane [ `System.AppDomain` ](https://github.com/dotnet/corefx/blob/master/src/Common/src/CoreLib/System/AppDomain.cs) w odniesieniu do źródła odwołania w repozytorium usługi [GitHub/corefx](https://github.com/dotnet/corefx)w serwisie, pamiętaj, aby wybrać gałąź zgodną z zaimplementowaną wersją.

## <a name="remoting"></a>Komunikacji zdalnej

Komunikacja zdalna .NET została zidentyfikowana jako problematyczna architektura. Jest on używany do komunikacji między domenami, która nie jest już obsługiwana. Ponadto komunikacja zdalna wymaga obsługi środowiska uruchomieniowego, co jest kosztowne do utrzymania. Z tego względu komunikacja zdalna .NET nie jest obsługiwana w przypadku platformy .NET Core i nie planuje się jej dodawania w przyszłości.

W przypadku komunikacji między procesami należy wziąć pod uwagę mechanizmy komunikacji między procesami (IPC) jako alternatywę dla usług zdalnych <xref:System.IO.Pipes> , takich <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> jak lub klasy.

Na wielu maszynach Użyj rozwiązania sieciowego jako alternatywy. Najlepiej użyć niskiego obciążenia protokołu zwykłego tekstu, takiego jak HTTP. Serwer [sieci Web Kestrel](https://docs.microsoft.com/aspnet/core/fundamentals/servers/kestrel), serwer sieci Web używany przez ASP.NET Core, jest opcją w tym miejscu. Należy również rozważyć <xref:System.Net.Sockets> użycie w przypadku scenariuszy opartych na sieci i wielu maszynach. Aby uzyskać więcej informacji, [Zobacz projekty deweloperskie programu .NET Open Source: Obsługa](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging)komunikatów.

## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)

W przypadku korzystania z trybu piaskownicy, który polega na środowisku uruchomieniowym lub środowisku, aby ograniczyć zasoby, których zarządzana aplikacja lub biblioteka jest uruchomiona, [nie jest obsługiwane w .NET Framework](../../framework/misc/code-access-security.md) i dlatego nie jest również obsługiwane w programie .NET Core. W .NET Framework jest zbyt wiele przypadków i środowisko uruchomieniowe, w którym występuje podniesienie uprawnień, aby kontynuować traktowanie urzędów certyfikacji jako granic zabezpieczeń. Ponadto urzędy certyfikacji czynią implementację bardziej skomplikowaną i często mają prawidłowy wpływ na wydajność aplikacji, które nie będą używane.

Użyj granic zabezpieczeń zapewnianych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników do uruchamiania procesów z minimalnym zestawem uprawnień.

## <a name="security-transparency"></a>Przejrzystość zabezpieczeń

Podobnie jak w przypadku urzędów certyfikacji, przezroczystość zabezpieczeń oddziela kod w trybie piaskownicy od krytycznego kodu zabezpieczeń w sposób deklaratywny, ale [nie jest już obsługiwany jako granica zabezpieczeń](../../framework/misc/security-transparent-code.md). Ta funkcja jest intensywnie używana przez program Silverlight. 

Użyj granic zabezpieczeń zapewnianych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników do uruchamiania procesów z najmniej określonym zestawem uprawnień.

## <a name="systementerpriseservices"></a>System.EnterpriseServices

System. EnterpriseServices (COM+) nie jest obsługiwany przez platformę .NET Core.

>[!div class="step-by-step"]
>[Next](third-party-deps.md)
