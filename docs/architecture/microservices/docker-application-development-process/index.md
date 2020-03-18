---
title: Proces tworzenia aplikacji opartych na platformie Docker
description: Uzyskaj ogólny przegląd opcji tworzenia aplikacji opartych na platformie Docker. Korzystanie z programu Visual Studio dla systemu Windows, programu Visual Studio dla komputerów Mac lub programu Visual Studio Code do obsługi wieloplatformowej (Windows, macOS i Linux).
ms.date: 01/30/2020
ms.openlocfilehash: 799aa6fc742a8fb763ec5a7ae3cf3f70f89bed6d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77502720"
---
# <a name="development-process-for-docker-based-applications"></a>Proces tworzenia aplikacji opartych na platformie Docker

*Tworzenie konteneryzowanych aplikacji .NET tak, jak chcesz, albo zintegrowane środowisko programistyczne (IDE) koncentruje się na visual studio i visual studio narzędzi dla platformy Docker lub CLI/Editor koncentruje się na docker CLI i Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Środowisko deweloperskie dla aplikacji platformy Docker

### <a name="development-tool-choices-ide-or-editor"></a>Opcje narzędzi programistycznych: IDE lub edytor

Niezależnie od tego, czy wolisz pełny i wydajny ide, czy lekki i zwinny edytor, firma Microsoft ma narzędzia, których można używać do tworzenia aplikacji Platformy Docker.

**Visual Studio (dla systemu Windows).** Program programistur aplikacji platformy Docker oparty na platformie .NET Core 3.1 w programie Visual Studio wymaga programu Visual Studio 2019 w wersji 16.4 lub nowszej. Visual Studio 2019 jest wyposażone w narzędzia do platformy Docker już wbudowane. Narzędzia do platformy Docker umożliwiają tworzenie, uruchamianie i weryfikowanie aplikacji bezpośrednio w docelowym środowisku platformy Docker. Można nacisnąć klawisz F5, aby uruchomić i debugować aplikację (pojedynczy kontener lub wiele kontenerów) bezpośrednio do hosta platformy Docker lub naciśnij klawisze CTRL+F5, aby edytować i odświeżać aplikację bez konieczności odbudowywania kontenera. Jest to najbardziej zaawansowany wybór programistycznych dla aplikacji opartych na platformie Docker.

**Visual Studio dla komputerów Mac.** Jest to IDE, ewolucja Xamarin Studio, działająca w systemie macOS. W przypadku programu .NET Core 3.1 wymaga wersji 8.4 lub nowszej. Powinien to być preferowany wybór dla deweloperów pracujących na komputerach z systemem macOS, którzy również chcą używać zaawansowanego ide.

**Kod programu Visual Studio i docker CLI**. Jeśli wolisz edytor lekki i międzyplatformowy, który obsługuje dowolny język rozwoju, można użyć kodu programu Visual Studio i docker CLI. Jest to wieloplatformowe podejście programistyczne dla systemów macOS, Linux i Windows. Ponadto Visual Studio Code obsługuje rozszerzenia platformy Docker, takie jak IntelliSense dla plików dockerfiles i zadania skrótów do uruchamiania poleceń platformy Docker z edytora.

Instalując [program Docker Desktop Community Edition (CE),](https://hub.docker.com/search/?type=edition&offering=community)można użyć jednego środowiska docker CLI do tworzenia aplikacji dla systemów Windows i Linux.

### <a name="additional-resources"></a>Zasoby dodatkowe

- **Studio wizualne**. Oficjalna strona internetowa. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Program Visual Studio Code** Oficjalna strona internetowa. \
  <https://code.visualstudio.com/download>

- **Pulpit platformy Docker dla wersji społecznościowej systemu Windows (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- **Docker Desktop dla komputerów Mac Community Edition (CE)** \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Języki i struktury platform .NET dla kontenerów platformy Docker

Jak wspomniano we wcześniejszych sekcjach tego przewodnika, można użyć .NET Framework, .NET Core lub projektu mono open source podczas opracowywania aplikacji platformy Docker konteneryzowanych .NET. Można opracować\#w\#języku C, F lub Visual Basic podczas określania pola kontenerów systemu Linux lub Windows, w zależności od tego, która platforma .NET jest używana. Aby uzyskać więcej informacji about.NET języków, zobacz wpis w blogu [Strategia języka .NET](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Poprzedni](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[następny](docker-app-development-workflow.md)
