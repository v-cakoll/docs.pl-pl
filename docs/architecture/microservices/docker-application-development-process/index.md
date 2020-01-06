---
title: Proces opracowywania aplikacji opartych na platformie Docker
description: Zapoznaj się z ogólnym omówieniem opcji tworzenia aplikacji opartych na platformie Docker. Korzystanie z wybranego programu Visual Studio dla systemu Windows, Visual Studio dla komputerów Mac lub Visual Studio Code w celu uzyskania pomocy technicznej dla wielu platform (Windows, macOS i Linux).
ms.date: 09/27/2018
ms.openlocfilehash: 95e940371f4dbef3b3a8f327c13acbbc55ff29ef
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75337698"
---
# <a name="development-process-for-docker-based-applications"></a>Proces opracowywania aplikacji opartych na platformie Docker

*Tworzenie kontenerów aplikacji platformy .NET w taki sam sposób, jak na przykład środowisko IDE skoncentrowane na programie Visual Studio i Visual Studio Tools for Docker lub CLI/Edytor, które koncentrują się na interfejsie wiersza polecenia platformy Docker i Visual Studio Code.*

## <a name="development-environment-for-docker-apps"></a>Środowisko deweloperskie dla aplikacji platformy Docker

### <a name="development-tool-choices-ide-or-editor"></a>Wybór narzędzi programistycznych: IDE lub Edytor

Bez względu na to, czy wolisz pełną i wydajną platformę IDE, czy też Edytor uproszczony i Agile, firma Microsoft oferuje narzędzia, których można użyć do tworzenia aplikacji platformy Docker.

**Visual Studio (dla systemu Windows).** W przypadku tworzenia aplikacji opartych na platformie Docker za pomocą programu Visual Studio zaleca się używanie programu Visual Studio 2017 w wersji 15,7 lub nowszej, który zawiera narzędzia dla platformy Docker już wbudowane. Narzędzia dla platformy Docker umożliwiają tworzenie, uruchamianie i Weryfikowanie aplikacji bezpośrednio w docelowym środowisku platformy Docker. Naciśnij klawisz F5, aby uruchomić i debugować aplikację (pojedynczy kontener lub wiele kontenerów) bezpośrednio na hoście platformy Docker lub naciśnij kombinację klawiszy CTRL + F5, aby edytować i odświeżać aplikację bez konieczności ponownego kompilowania kontenera. Jest to najbardziej zaawansowany wybór dla aplikacji opartych na platformie Docker.

**Visual Studio for Mac.** Jest to środowisko IDE, ewolucja Xamarin Studio, działające w macOS i obsługuje platformę Docker od połowy 2017. Powinno to być preferowany wybór dla deweloperów pracujących na maszynach macOS, którzy chcą również korzystać z zaawansowanego środowiska IDE.

**Visual Studio Code i interfejs wiersza polecenia platformy Docker**. Jeśli wolisz uproszczony i Międzyplatformowy Edytor obsługujący dowolny język programowania, możesz użyć kodu Microsoft Visual Studio (VS Code) i interfejsu wiersza polecenia platformy Docker. Jest to międzyplatformowe podejście do tworzenia aplikacji dla systemów macOS, Linux i Windows. Ponadto Visual Studio Code obsługuje rozszerzenia dla platformy Docker, takie jak IntelliSense do wieloetapowe dockerfile i zadań skrótów do uruchamiania poleceń platformy Docker z edytora.

Instalując program [Docker Desktop Community Edition (CE)](https://hub.docker.com/search/?type=edition&offering=community), można użyć jednego interfejsu wiersza polecenia platformy Docker do kompilowania aplikacji dla systemów Windows i Linux.

### <a name="additional-resources"></a>Dodatkowe zasoby

- Program **Visual Studio**. Oficjalna lokacja. \
  [https://visualstudio.microsoft.com/vs/](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link)

- **Program Visual Studio Code** Oficjalna lokacja. \
  <https://code.visualstudio.com/download>

- **Pulpit Docker dla systemu Windows Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-windows](https://hub.docker.com/editions/community/docker-ce-desktop-windows)

- Rozwiązanie **Docker Desktop dla komputerów Mac Community Edition (CE)**  \
  [https://hub.docker.com/editions/community/docker-ce-desktop-mac](https://hub.docker.com/editions/community/docker-ce-desktop-mac)

## <a name="net-languages-and-frameworks-for-docker-containers"></a>Języki i struktury platformy .NET dla kontenerów platformy Docker

Jak wspomniano w poprzednich sekcjach tego przewodnika, można użyć .NET Framework, .NET Core lub projektu mono typu open source podczas tworzenia kontenerów platformy Docker z platformą .NET. W zależności od tego, które środowisko .NET Framework jest używane, można opracowywać w języku C\#, F\#lub Visual Basic. Aby uzyskać więcej szczegółów na temat języków about.NET, zobacz wpis w blogu [strategia języka .NET](https://devblogs.microsoft.com/dotnet/the-net-language-strategy/).

>[!div class="step-by-step"]
>[Poprzedni](../architect-microservice-container-applications/scalable-available-multi-container-microservice-applications.md)
>[Następny](docker-app-development-workflow.md)
