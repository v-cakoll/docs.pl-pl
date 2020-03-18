---
title: Narzędzia programu Visual Studio dla platformy Docker w systemie Windows
description: Poznaj narzędzia platformy Docker dostępne w programie Visual Studio 2017 w wersji 15.7 i nowszych.
ms.date: 02/15/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 2b6fdc33f9cf850cf9e52fca4a1a9754cd412567
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "70295809"
---
# <a name="use-docker-tools-in-visual-studio-2017-on-windows"></a>Korzystanie z narzędzi platformy Docker w programie Visual Studio 2017 w systemie Windows

Przepływ pracy dewelopera podczas korzystania z narzędzi platformy Docker zawartych w programie Visual Studio 2017 w wersji 15.7 i nowszych jest podobny do korzystania z kodu programu Visual Studio i interfejsu interfejsu i ze siatek platformy Docker (w rzeczywistości jest on oparty na tym samym platformie Docker CLI), ale łatwiej jest rozpocząć, upraszcza proces i zapewnia większą wydajność zadań kompilacji, uruchamiania i komponowania. Można również uruchamiać i debugować `F5` `Ctrl+F5` kontenery za pośrednictwem zwykłych i kluczy z programu Visual Studio. Można nawet debugować całe rozwiązanie, jeśli jego `docker-compose.yml` kontenery są zdefiniowane w tym samym pliku na poziomie rozwiązania.

## <a name="configure-your-local-environment"></a>Konfigurowanie środowiska lokalnego

W najnowszych wersjach platformy Docker dla systemu Windows tworzenie aplikacji platformy Docker jest łatwiejsze niż kiedykolwiek wcześniej, ponieważ konfiguracja jest prosta, jak wyjaśniono w poniższych odwołaniach.

> [!TIP]
> Aby dowiedzieć się więcej o instalowaniu<https://docs.docker.com/docker-for-windows/>platformy Docker dla systemu Windows, przejdź do ( ).

## <a name="docker-support-in-visual-studio-2017"></a>Obsługa platformy Docker w programie Visual Studio 2017

Istnieją dwa poziomy obsługi platformy Docker, które można dodać do projektu. W ASP.NET projektów Core można `Dockerfile` po prostu dodać plik do projektu, włączając obsługę platformy Docker. Następny poziom jest obsługa aranżacji `Dockerfile` kontenera, który dodaje do projektu (jeśli jeszcze nie istnieje) i `docker-compose.yml` plik na poziomie rozwiązania. Obsługa aranżacji kontenerów za pośrednictwem platformy Docker Compose jest domyślnie dodawana w programie Visual Studio 2017 w wersjach od 15.0 do 15.7. Obsługa aranżacji kontenerów to funkcja opt-in w programie Visual Studio 2017 w wersji 15.8 lub nowszej. Wersja 15.8 później obsługuje docker compose i sieci szkieletowej usług.

Polecenia **Dodaj > docker Support** i Add > Container **Orchestrator Support** polecenia znajdują się w menu prawym przyciskiem myszy (lub menu kontekstowym) węzła projektu dla projektu ASP.NET Core w **Eksploratorze rozwiązań**, jak pokazano na rysunku 4-31:

![Opcja menu Dodawanie platformy Docker w programie Visual Studio](./media/add-docker-support-menu.png)

**Rysunek 4-31**. Dodawanie obsługi platformy Docker do projektu programu Visual Studio 2017

### <a name="add-docker-support"></a>Dodawanie obsługi platformy Docker

Obsługę platformy Docker można dodać do istniejącego projektu ASP.NET Core, wybierając pozycję **Dodaj** > **obsługę platformy Docker** w **Eksploratorze rozwiązań**. Podczas tworzenia projektu można również włączyć obsługę platformy Docker, wybierając opcję **Włącz obsługę platformy Docker** w oknie dialogowym **Nowa ASP.NET Podstawowa aplikacja sieci Web,** które zostanie otwarte po kliknięciu przycisku **OK** w oknie dialogowym **Nowy projekt,** jak pokazano na rysunku 4–32.

![Włącz obsługę platformy Docker dla nowej aplikacji sieci web ASP.NET Core w programie Visual Studio](./media/enable-docker-support-visual-studio.png)

**Rysunek 4-32**. Włącz obsługę platformy Docker podczas tworzenia projektu w programie Visual Studio 2017

Po dodaniu lub włączeniu obsługi platformy Docker program Visual Studio dodaje plik *Dockerfile* do projektu.

> [!NOTE]
> Po włączeniu docker compose support podczas tworzenia projektu dla ASP.NET projektu (.NET Framework, a nie .NET Core projektu), jak pokazano na rysunku 4-33, obsługa aranżacji kontenera jest również dodawany.

![Włączanie obsługi platformy Docker w celu skomponowania projektu ASP.NET](media/enable-docker-compose-support.png)

**Rysunek 4-33**. Włączanie obsługi platformy Docker Compose dla ASP.NET projektu w programie Visual Studio 2017

### <a name="add-container-orchestration-support"></a>Dodawanie obsługi aranżacji kontenerów

Jeśli chcesz skomponować rozwiązanie wielokontenerowe, dodaj obsługę aranżacji kontenerów do swoich projektów. Dzięki temu można uruchomić i debugować grupę kontenerów (całe rozwiązanie) w tym samym czasie, jeśli są one zdefiniowane w tym samym pliku *docker-compose.yml.*

Aby dodać obsługę aranżacji kontenerów, kliknij prawym przyciskiem myszy węzeł rozwiązania lub projektu w **Eksploratorze rozwiązań**i wybierz polecenie **Dodaj > obsługę aranżacji kontenerów**. Następnie wybierz **opcję Docker Compose** lub **Service Fabric** do zarządzania kontenerami.

Po dodaniu obsługi aranżacji kontenerów do projektu zostanie wyświetlony plik Dockerfile dodany do projektu oraz folder **docker-compose** dodany do rozwiązania w **Eksploratorze rozwiązań**, jak pokazano na rysunku 4–34:

![Pliki platformy Docker w Eksploratorze rozwiązań w programie Visual Studio](media/docker-support-solution-explorer.png)

**Rysunek 4-34**. Pliki platformy Docker w Eksploratorze rozwiązań w programie Visual Studio 2017

Jeśli *docker-compose.yml* już istnieje, Visual Studio po prostu dodaje wymagane wiersze kodu konfiguracji do niego.

## <a name="configure-docker-tools"></a>Konfigurowanie narzędzi do platformy Docker

Z menu głównego wybierz polecenie **Narzędzia > opcje**i rozwiń pozycję Narzędzia **kontenerów > Ustawienia**. Zostaną wyświetlone ustawienia narzędzi kontenera.

![Opcje narzędzi platformy Docker programu Visual Studio, pokazujące: Automatycznie ściąganie wymaganych obrazów platformy Docker przy obciążeniu projektu, automatyczne uruchamianie kontenerów w tle, automatyczne zabijanie kontenerów przy zamknięciu rozwiązania i nie monitowanie o ufanie certyfikatowi SSL.](./media/visual-studio-docker-tools-options.png)

**Rysunek 4-35**. Opcje narzędzi platformy Docker

Poniższa tabela może pomóc w podjęciu decyzji, jak ustawić te opcje.

| Nazwa | Ustawienie domyślne | Dotyczy: | Opis |
| -----|:---------------:|:----------:| ----------- |
| Automatyczne ściąganie wymaganych obrazów platformy Docker przy obciążeniu projektu | Włączone | Docker Compose | Aby zwiększyć wydajność podczas ładowania projektów, visual studio rozpocznie operację ściągania platformy Docker w tle, tak aby gdy wszystko będzie gotowe do uruchomienia kodu, obraz jest już pobrany lub w trakcie pobierania. Jeśli dopiero ładujesz projekty i kod przeglądania, możesz wyłączyć tę możliwość, aby uniknąć pobierania obrazów kontenerów, których nie potrzebujesz. |
| Automatyczne uruchamianie kontenerów w tle | Włączone | Docker Compose | Ponownie dla zwiększenia wydajności, Visual Studio tworzy kontener z instalacji woluminu gotowy do tworzenia i uruchamiania kontenera. Jeśli chcesz kontrolować, kiedy kontener jest tworzony, wyłącz tę możliwość. |
| Automatyczne zabijanie pojemników na zamknięciu rozwiązania | Włączone | Docker Compose | Wyłącz tę możliwość, jeśli chcesz kontenery dla rozwiązania, aby kontynuować po zamknięciu rozwiązania lub zamknięcia programu Visual Studio. |
| Nie monituj o zaufanie certyfikatu SSL hosta lokalnego | Wyłączone | ASP.NET projekty Core 2.2 | Jeśli certyfikat SSL hosta lokalnego nie jest zaufany, program Visual Studio będzie monitować przy każdym uruchomieniu projektu, chyba że to pole wyboru jest zaznaczone. |

> [!WARNING]
> Jeśli certyfikat SSL hosta lokalnego nie jest zaufany i zaznaczysz to pole, aby pominąć monitowanie, żądania sieci Web HTTPS mogą zakończyć się niepowodzeniem w czasie wykonywania w aplikacji lub usłudze. W takim przypadku należy odznaczyć pole wyboru **Nie monituj,** uruchom projekt i wskaż zaufanie w wierszu polecenia.

> [!TIP]
> Aby uzyskać więcej informacji na temat implementacji usług i korzystania z narzędzi programu Visual Studio dla platformy Docker, przeczytaj następujące artykuły:
>
>Debugowanie aplikacji w lokalnym kontenerze platformy Docker:<https://docs.microsoft.com/azure/vs-azure-tools-docker-edit-and-refresh>
>
>Wdrażanie kontenera ASP.NET w rejestrze kontenerów przy użyciu programu Visual Studio:<https://docs.microsoft.com/azure/vs-azure-tools-docker-hosting-web-apps-in-docker>

>[!div class="step-by-step"]
>[Poprzedni](docker-apps-inner-loop-workflow.md)
>[następny](set-up-windows-containers-with-powershell.md)
