---
title: "Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio w systemie Windows)"
description: "Cykl życia aplikacji konteneryzowanych Docker z platformy firmy Microsoft i narzędzia"
keywords: "Docker, Mikrousług, ASP.NET, kontenera"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.openlocfilehash: d7a24633f5857bc5b72ebab42020627c645f4302
ms.sourcegitcommit: 6f49c973f62855ffd6c4a322903e7dd50c5c1b50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/23/2017
---
# <a name="using-visual-studio-tools-for-docker-visual-studio-on-windows"></a>Za pomocą narzędzi Visual Studio Tools for Docker (Visual Studio w systemie Windows)

Przepływ pracy deweloperów, gdy za pomocą narzędzi Visual Studio Tools dla Docker jest podobny do przepływu pracy, korzystając z programu Visual Studio Code i interfejsu wiersza polecenia Docker (w rzeczywistości go opiera się na tym samym interfejsu wiersza polecenia Docker), ale jest łatwiej rozpocząć pracę, upraszcza proces i zapewnia większą wydajność dla kompilacji, uruchomić i tworzą zadania. Istnieje również możliwość wykonania i debugowanie kontenerów za pomocą prostego akcji, takich jak F5 i Ctrl + F5 w programie Visual Studio. Jeszcze bardziej z programu Visual Studio 2017 r, oprócz możliwości by przeprowadzić debugowanie jeden kontener, również można uruchomić i debugowania grupy kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one zdefiniowane w ten sam plik docker-compose.yml na poziomie rozwiązania.

## <a name="configuring-your-local-environment"></a>Konfigurowanie środowiska lokalnego

Najnowsze wersje Docker dla systemu Windows jest łatwiejsze niż kiedykolwiek do opracowywania aplikacji Docker ponieważ Instalator jest proste, jak opisano w następujących odwołań.

**Aby dowiedzieć się więcej:** Aby dowiedzieć się więcej na temat instalowania Docker dla systemu Windows, przejdź do <https://docs.docker.com/docker-for-windows/>.

Jeśli używasz programu Visual Studio 2015, musi mieć aktualizacji 3 lub nowszym oraz programu Visual Studio Tools for Docker.

**Aby dowiedzieć się więcej:** instrukcje dotyczące instalowania programu Visual Studio, przejdź do [https://www.visualstudio.com/ \ produkty/vs-2015-— wersje produktu](https://www.visualstudio.com/products/vs-2015-product-editions).

Aby wyświetlić więcej informacji na temat instalowania programu Visual Studio Tools for Docker, przejdź do <http://aka.ms/vstoolsfordocker> i <https://docs.microsoft.com/dotnet/articles/core/docker/visual-studio-tools-for-docker>.

Jeśli używasz programu Visual Studio 2017 Docker obsługi jest już dołączony.

## <a name="using-docker-tools-in-visual-studio-2015"></a>Za pomocą narzędzi Docker w programie Visual Studio 2015

Visual Studio Tools for Docker zapewnia spójny sposób rozwijać i zweryfikować lokalnie kontenerów Docker dla systemu Linux na hoście systemu Linux Docker lub maszyny Wirtualnej lub kontenerów systemu Windows bezpośrednio w systemie Windows.

Jeśli używasz jeden kontener, w pierwszej kolejności należy rozpocząć jest włączenie obsługi Docker do projektu platformy .NET Core. Aby to zrobić, kliknij prawym przyciskiem myszy plik projektu, jak pokazano na rysunku 4-25.

![https://I1.visualstudiogallery.msdn.s-MSFT.com/0f5b2caa-ea00-41c8-b8a2-058c7da0b3e4/Image/File/205468/1/Add-docker-support.PNG](./media/image31.png)

Rysunek 4-25: włączania obsługi Docker projektu programu Visual Studio

## <a name="using-docker-tools-in-visual-studio-2017"></a>Za pomocą narzędzi Docker w programie Visual Studio 2017 r.

Po dodaniu obsługi Docker do projektu usługi w rozwiązaniu (zobacz rysunek 4-26) i Visual Studio jest nie tylko można dodać plik DockerFile plik do projektu, jego również jest dodanie usługi sekcji rozwiązania docker-compose.yml plików (lub tworzenia plików, jeśli nie zostały one istnieje). Jest to prosty sposób, aby rozpocząć tworzenie rozwiązania multicontainer; następnie można otwierać pliki docker-compose.yml i zaktualizować je z dodatkowych funkcji.

![](./media/image32.png)

Rysunek 4-26: włączania obsługi rozwiązania Docker w projekcie programu Visual Studio 2017 r.

Ta akcja dodaje plik DockerFile nie tylko do projektu, dodane również wymagana konfiguracja wiersze kodu do globalnego docker-compose.yml należy ustawić na poziomie rozwiązania.

Także można włączyć obsługę Docker podczas tworzenia projektu platformy ASP.NET Core w Visual Studio 2017 r, jak pokazano w rysunek 4-27.

![](./media/image33.png)

Rysunek 4-27: włączania obsługi Docker podczas tworzenia projektu

Po dodaniu obsługi Docker do rozwiązania w programie Visual Studio również zobaczysz nowe drzewo węzła w Eksploratorze rozwiązań z plikami dodano docker-compose.yml, jak pokazano w rysunek 4-28.

![](./media/image34.PNG)

Rysunek 4-28: docker-compose.yml plików jest teraz wyświetlany w Eksploratorze rozwiązań

Można wdrożyć multicontainer aplikacji przy użyciu pliku pojedynczego docker-compose.yml po uruchomieniu rozwiązania docker-compose; jednak Visual Studio dodaje grupę, więc można zastąpić wartości w zależności od środowiska (Programowanie i produkcja) i wykonywania typu (wersja i debugowania). Ta funkcja zostanie lepiej wyjaśnione w rozdziałach nowsze.

**Aby dowiedzieć się więcej:** Aby uzyskać więcej szczegółowych informacji o implementacji usług i korzystanie z programu Visual Studio Tools for Docker, przeczytaj następujące artykuły:

Kompilacji, debugowania, aktualizacji i odświeżanie aplikacji w kontenerze Docker lokalnego: [https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh/](https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh)

Wdrażanie kontenera ASP.NET z hostem zdalnym Docker: [https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker/](https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker)


>[!div class="step-by-step"]
[Poprzednie] (docker aplikacje — wewnętrzny pętli workflow.md) [dalej] (set-up-windows-containers-with-powershell.md)
