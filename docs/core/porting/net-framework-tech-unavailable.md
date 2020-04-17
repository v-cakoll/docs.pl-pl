---
title: Technologie .NET Framework są niedostępne w programie .NET Core
titleSuffix: ''
description: Dowiedz się więcej o technologiach platformy .NET Framework, które są niedostępne w programie .NET Core
author: cartermp
ms.date: 04/30/2019
ms.openlocfilehash: 7dfec63870950f12ec933ebf09041b3c8ce2cbb5
ms.sourcegitcommit: d9470d8b2278b33108332c05224d86049cb9484b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/17/2020
ms.locfileid: "81607800"
---
# <a name="net-framework-technologies-unavailable-on-net-core"></a>Technologie .NET Framework są niedostępne w programie .NET Core

Kilka technologii dostępnych dla bibliotek programu .NET Framework nie jest dostępnych do użytku z programem .NET Core, takich jak AppDomains, Remoting, Code Access Security (CAS), Security Transparency i System.EnterpriseServices. Jeśli biblioteki opierają się na co najmniej jednej z tych technologii, należy wziąć pod uwagę alternatywne podejścia opisane poniżej. Aby uzyskać więcej informacji na temat zgodności interfejsu API, zobacz [.NET Core breaking changes](../compatibility/breaking-changes.md).

Tylko dlatego, że interfejs API lub technologii nie jest obecnie zaimplementowana nie oznacza, że jest celowo nieobsługiwane. Przeszukaj repozytoria GitHub dla platformy .NET Core, aby sprawdzić, czy napotkany konkretny problem jest według projektu. Jeśli nie znajdziesz takiego wskaźnika, złóż problem w [repozytorium dotnet/runtime,](https://github.com/dotnet/runtime/issues) aby poprosić o określone interfejsy API i technologie. Problemy, które są przenoszenie żądań są oznaczone [etykietą port-core.](https://github.com/dotnet/runtime/labels/port-to-core)

## <a name="appdomains"></a>AppDomains (Aplikacje)

Domeny aplikacji (AppDomains) izolują aplikacje od siebie. AppDomains wymagają obsługi środowiska uruchomieniowego i są zazwyczaj dość drogie. Tworzenie dodatkowych domen aplikacji nie jest obsługiwane i nie ma żadnych planów, aby dodać tę funkcję w przyszłości. W przypadku izolacji kodu należy użyć oddzielnych procesów lub kontenerów jako alternatywy. Aby dynamicznie ładować <xref:System.Runtime.Loader.AssemblyLoadContext> złożenia, należy użyć klasy.

Aby ułatwić migrację kodu z platformy .NET Framework, <xref:System.AppDomain> program .NET Core udostępnia część powierzchni interfejsu API. <xref:System.AppDomain.UnhandledException?displayProperty=nameWithType>Niektóre interfejsy API działają normalnie (na przykład), niektórzy członkowie <xref:System.AppDomain.SetCachePath%2A>nic nie robią <xref:System.PlatformNotSupportedException> (na przykład), a niektórzy rzucają (na <xref:System.AppDomain.CreateDomain%2A>przykład). Sprawdź typy używane względem [ `System.AppDomain` źródła referencyjnego](https://github.com/dotnet/runtime/blob/master/src/libraries/System.Private.CoreLib/src/System/AppDomain.cs) w [repozytorium github dotnet/runtime](https://github.com/dotnet/runtime). Upewnij się, aby wybrać gałąź, która pasuje do zaimplementowanej wersji.

## <a name="remoting"></a>Usług zdalnych

.NET Komunikacji zdalnej został zidentyfikowany jako problematyczna architektura. Jest on używany do komunikacji między aplikacjamiDomain, który nie jest już obsługiwany. Ponadto komunikacji zdalnej wymaga obsługi środowiska uruchomieniowego, który jest kosztowne w utrzymaniu. Z tych powodów .NET Remoting nie jest obsługiwany w programie .NET Core i nie planujemy dodawania pomocy technicznej dla niego w przyszłości.

W przypadku komunikacji między procesami należy wziąć pod uwagę mechanizmy komunikacji między <xref:System.IO.Pipes> procesami <xref:System.IO.MemoryMappedFiles.MemoryMappedFile> (IPC) jako alternatywę dla komunikacji zdalnej, takie jak klasa lub klasa.

Na różnych komputerach użyj rozwiązania sieciowego jako alternatywy. Najlepiej użyć protokołu zwykłego tekstu o niskim poziomie napowietrznym, takiego jak HTTP. [Kestrel serwer www](/aspnet/core/fundamentals/servers/kestrel), serwer www używany przez ASP.NET Core, jest opcja tutaj. Należy również <xref:System.Net.Sockets> rozważyć użycie w scenariuszach opartych na sieci, między komputerami. Aby uzyskać więcej opcji, zobacz [.NET Open Source Developer Projects: Messaging](https://github.com/Microsoft/dotnet/blob/master/dotnet-developer-projects.md#messaging).

## <a name="code-access-security-cas"></a>Zabezpieczenia dostępu kodu (CAS)

Piaskownica, która opiera się na środowisko uruchomieniowe lub struktury, aby ograniczyć zasoby, które aplikacja zarządzana lub biblioteka używa lub uruchamia, [nie jest obsługiwana w programie .NET Framework](../../framework/misc/code-access-security.md) i dlatego nie jest również obsługiwana w programie .NET Core. Istnieje zbyt wiele przypadków w .NET Framework i środowiska wykonawczego, w którym występuje podniesienie uprawnień, aby kontynuować traktowanie cas jako granicy zabezpieczeń. Ponadto CAS sprawia, że implementacja bardziej skomplikowane i często ma wpływ na poprawność wydajności dla aplikacji, które nie zamierzają go używać.

Użyj granic zabezpieczeń dostarczonych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników, do uruchamiania procesów z minimalnym zestawem uprawnień.

## <a name="security-transparency"></a>Przejrzystość zabezpieczeń

Podobnie jak CAS, przezroczystość zabezpieczeń oddziela kod w trybie piaskownicy od kodu krytycznego zabezpieczeń w sposób deklaratywny, ale nie jest [już obsługiwany jako granica zabezpieczeń.](../../framework/misc/security-transparent-code.md) Ta funkcja jest intensywnie używana przez program Silverlight.

Użyj granic zabezpieczeń dostarczonych przez system operacyjny, takich jak wirtualizacja, kontenery lub konta użytkowników, do uruchamiania procesów z najmniejszym zestawem uprawnień.

## <a name="systementerpriseservices"></a>System.enterpriseservices

System.EnterpriseServices (COM+) nie jest obsługiwany przez program .NET Core.

## <a name="see-also"></a>Zobacz też

- [Omówienie przenoszenia z programu .NET Framework do platformy .NET Core](../porting/index.md)
