---
title: Visual Studio Tools for Docker w systemie Windows
description: Poznaj narzędzia platformy Docker dostępne w programie Visual Studio 2017 w wersji 15,7 lub nowszej.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "70295809"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Korzystanie z narzędzi platformy Docker w programie Visual Studio 2017 w systemie Windows

Przepływ pracy dla deweloperów w przypadku korzystania z narzędzi platformy Docker zawartych w programie Visual Studio 2017 w wersji 15,7 lub nowszej jest podobny do używania Visual Studio Code i interfejsu wiersza polecenia platformy Docker (w rzeczywistości jest on oparty na tym samym interfejsie wiersza polecenia platformy Docker), ale łatwiej jest rozpocząć pracę, uprościć proces i zapewnia większą produktywność dla zadań kompilowania, uruchamiania i redagowania. Może również uruchamiać i debugować kontenery za pomocą zwykłych `F5` i kluczy `Ctrl+F5` z programu Visual Studio. Można nawet debugować całe rozwiązanie, jeśli jego kontenery są zdefiniowane w tym samym pliku `docker-compose.yml` na poziomie rozwiązania.

## <a name="configure-your-local-environment"></a>Konfigurowanie środowiska lokalnego

Najnowsze wersje Docker for Windows ułatwiają tworzenie aplikacji platformy Docker, ponieważ konfiguracja jest prosta, zgodnie z opisem w poniższych odwołaniach.

> [!TIP]
> Aby dowiedzieć się więcej o instalowaniu Docker for Windows, przejdź do (<https://docs.docker.com/docker-for-windows/>).

## <a name="docker-support-in-visual-studio-2017"></a>Obsługa platformy Docker w programie Visual Studio 2017

Istnieją dwa poziomy obsługi platformy Docker, które można dodać do projektu. W projektach ASP.NET Core można po prostu dodać plik `Dockerfile` do projektu, włączając obsługę platformy Docker. Następnym poziomem jest obsługa aranżacji kontenerów, która dodaje `Dockerfile` do projektu (jeśli jeszcze nie istnieje) i plik `docker-compose.yml` na poziomie rozwiązania. Obsługa aranżacji kontenerów za pośrednictwem Docker Compose jest domyślnie dodawana w programie Visual Studio 2017 w wersji 15,0 do 15,7. Obsługa aranżacji kontenerów to funkcja opcjonalna w programie Visual Studio 2017 w wersji 15,8 lub nowszej. W wersji 15,8 nowszej Docker Compose i Service Fabric.

Polecenia **dodaj > Docker support** i **Dodawanie > kontenerów pomocy technicznej Orchestrator** znajdują się w menu rozwijanym prawym przyciskiem myszy (lub w menu kontekstowym) węzła projektu dla projektu ASP.NET Core w **Eksplorator rozwiązań**, jak pokazano na rysunku 4-31:

![Opcja menu Dodaj obsługę platformy Docker w programie Visual Studio](./media/add-docker-support-menu.png)

**Rysunek 4-31**. Dodawanie obsługi platformy Docker do projektu programu Visual Studio 2017

### <a name="add-docker-support"></a>Dodaj obsługę platformy Docker

Obsługę platformy Docker można dodać do istniejącego projektu ASP.NET Core, wybierając pozycję **dodaj** > **obsługę platformy docker** w **Eksplorator rozwiązań**. Możesz również włączyć obsługę platformy Docker podczas tworzenia projektu, wybierając opcję **Włącz obsługę platformy Docker** w oknie dialogowym **Nowa aplikacja sieci Web ASP.NET Core** , które zostanie otwarte po kliknięciu przycisku **OK** w oknie dialogowym **nowy projekt** , jak pokazano na rysunku 4-32.

![Włącz obsługę platformy Docker dla nowej aplikacji internetowej ASP.NET Core w programie Visual Studio](./media/enable-docker-support-visual-studio.png)

**Rysunek 4-32**. Włącz obsługę platformy Docker podczas tworzenia projektu w programie Visual Studio 2017

Po dodaniu lub włączeniu obsługi platformy Docker program Visual Studio dodaje plik *pliku dockerfile* do projektu.

> [!NOTE]
> Po włączeniu obsługi Docker Compose podczas tworzenia projektu dla projektu ASP.NET (.NET Framework, a nie projektu .NET Core), jak pokazano na rysunku 4-33, dodano również obsługę aranżacji kontenerów.

![Włącz obsługę redagowania platformy Docker dla projektu ASP.NET](media/enable-docker-compose-support.png)

**Rysunek 4-33**. Włączanie obsługi Docker Compose dla projektu ASP.NET w programie Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Dodawanie obsługi aranżacji kontenera

Jeśli chcesz utworzyć rozwiązanie z obsługą kilku kontenerów, Dodaj obsługę aranżacji kontenera do projektów. Dzięki temu można uruchamiać i debugować grupę kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one zdefiniowane w tym samym pliku *Docker-Compose. yml* .

Aby dodać obsługę aranżacji kontenera, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksplorator rozwiązań**i wybierz polecenie **Dodaj obsługę aranżacji kontenerów >** . Następnie wybierz **Docker Compose** lub **Service Fabric** do zarządzania kontenerami.

Po dodaniu obsługi aranżacji kontenera do projektu zobaczysz pliku dockerfile dodaną do projektu i folderem **Docker-Zredaguj** do rozwiązania w **Eksplorator rozwiązań**, jak pokazano na rysunku 4-34:

![Pliki platformy Docker w Eksplorator rozwiązań w programie Visual Studio](media/docker-support-solution-explorer.png)

**Rysunek 4-34**. Pliki platformy Docker w Eksplorator rozwiązań w programie Visual Studio 2017

Jeśli *Docker-Compose. yml* już istnieje, Visual Studio dodaje do niego wymagane wiersze kodu konfiguracji.

## <a name="configure-docker-tools"></a>Konfigurowanie narzędzi platformy Docker

Z menu głównego wybierz polecenie **narzędzia > opcje**i rozwiń węzeł **Narzędzia kontenera > Ustawienia**. Zostaną wyświetlone ustawienia narzędzi kontenerów.

![Opcje narzędzi platformy Docker programu Visual Studio, pokazujące: Automatyczne ściąganie wymaganych obrazów platformy Docker podczas ładowania projektu, automatyczne uruchamianie kontenerów w tle, automatyczne zabicia kontenerów w ramach rozwiązania i nie Monituj o zaufanie certyfikatu SSL.](./media/visual-studio-docker-tools-options.png)

**Rysunek 4-35**. Opcje narzędzi platformy Docker

Poniższa tabela może pomóc określić, jak ustawić te opcje.

| Nazwa | Ustawienie domyślne | Dotyczy | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatycznie Ściągnij wymagane obrazy platformy Docker po załadowaniu projektu | Włączone | Docker Compose | W celu zwiększenia wydajności podczas ładowania projektów program Visual Studio rozpocznie operację ściągania platformy Docker w tle, dzięki czemu gdy wszystko będzie gotowe do uruchomienia kodu, obraz jest już pobrany lub proces pobierania. Jeśli właśnie ładujesz projekty i przeglądasz kod, możesz je wyłączyć, aby uniknąć pobierania niepotrzebnych obrazów kontenerów. |
| Automatycznie uruchamiaj kontenery w tle | Włączone | Docker Compose | W celu zwiększenia wydajności program Visual Studio tworzy kontener z instalacjami woluminów gotowymi do kompilowania i uruchamiania kontenera. Jeśli chcesz kontrolować czas tworzenia kontenera, wyłącz tę opcję. |
| Automatycznie Kasuj kontenery przy bliskim rozwiązaniu | Włączone | Docker Compose | Wyłącz tę opcję, jeśli chcesz, aby kontenery dla rozwiązania nadal działały po zamknięciu rozwiązania lub zamknięciu programu Visual Studio. |
| Nie Monituj o ufanie certyfikatowi SSL hosta lokalnego | Wyłączone | Projekty ASP.NET Core 2,2 | Jeśli certyfikat SSL hosta lokalnego nie jest zaufany, program Visual Studio wyświetli monit przy każdym uruchomieniu projektu, chyba że to pole wyboru jest zaznaczone. |

> [!WARNING]
> Jeśli certyfikat protokołu SSL hosta lokalnego nie jest zaufany i zaznaczasz pole, aby pominąć monitowanie, żądania sieci Web HTTPS mogą zakończyć się niepowodzeniem w czasie wykonywania w aplikacji lub usłudze. W takim przypadku Usuń zaznaczenie pola wyboru nie **Monituj** , Uruchom projekt i wskaż polecenie Ufaj w wierszu polecenia.

> [!TIP]
> Aby uzyskać więcej informacji na temat implementacji usług i używania Visual Studio Tools for Docker, przeczytaj następujące artykuły:
>
>Debugowanie aplikacji w lokalnym kontenerze platformy Docker: <https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Wdrażanie kontenera ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio: <https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Poprzedni](docker-apps-inner-loop-workflow.md)
>[Następny](set-up-windows-containers-with-powershell.md)
