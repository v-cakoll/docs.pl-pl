---
title: Uruchamianie aplikacji konsoli w Docker
description: Dowiedz się, jak wykonać istniejącej aplikacji konsoli .NET Framework i uruchom go w kontenerze Docker systemu Windows.
author: spboyer
ms.date: 09/28/2016
ms.assetid: 85cca1d5-c9a4-4eb2-93e6-4f878de07fd7
ms.openlocfilehash: 266c439163888962075f804a0f5651a8e7d83151
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33392687"
---
# <a name="running-console-applications-in-windows-containers"></a>Uruchamianie aplikacji konsoli w kontenerach systemu Windows

Aplikacje konsoli są używane dla wielu celów; proste wysyłanie kwerend stanu długotrwałej obraz dokumentu przetwarzania zadań. W każdym przypadku spełnia możliwość uruchamiania i skalowania tych aplikacji z ograniczeniami nabycia sprzętu, czasu uruchamiania lub uruchamianie wielu wystąpień.

Kontenery przenoszenie aplikacji konsoli do użycia Docker i Windows Server umożliwia uruchamiania tych aplikacji od stanu czystego, umożliwiając im wykonywanie operacji, a następnie zamknięcie prawidłowo. W tym temacie opisano kroki niezbędne do przeniesienia aplikacji konsoli do systemu Windows na podstawie kontenera i uruchomić go za pomocą skryptu programu PowerShell.

Przykładowa aplikacja konsolowa jest prosty przykład, w tym przypadku przyjmuje argument pytanie i zwraca losowe odpowiedzi. Może to potrwać `customer_id` przetworzyć ich podatki i tworzenie miniatur dla `image_url` argumentu.

Oprócz odpowiedzi `Environment.MachineName` został dodany do odpowiedzi wskazują różnice między uruchomieniem aplikacji lokalnie i w kontenerze systemu Windows. Podczas uruchamiania aplikacji lokalnie, nazwę komputera lokalnego ma zostać zwrócony, a podczas uruchamiania w kontenerze systemu Windows; Identyfikator sesji kontenera jest zwracana.

[Pełny przykład](https://github.com/dotnet/samples/tree/master/framework/docker/ConsoleRandomAnswerGenerator) jest dostępny w repozytorium dotnet/próbek w witrynie GitHub. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Należy zapoznać się z niektórych Docker warunki przed rozpoczęciem pracy na przenoszenie aplikacji do kontenera.

> A *Docker obrazu* jest tylko do odczytu szablonu, który definiuje środowisko uruchomionych kontenera, w tym system operacyjny (OS), składniki systemu i aplikacji.

Ważna cechą obrazy usługi Docker jest, że obrazy składają się z obrazu podstawowego. Każdy nowy obraz dodaje niewielki zestaw funkcji do istniejącego obrazu. 

> A *kontenera Docker* jest uruchomione wystąpienie obrazu. 

Skalowanie aplikacji przez uruchomienie tego samego obrazu w wielu kontenerów.
Koncepcyjnie jest podobny do uruchamiania tej samej aplikacji w wielu hostach.

Więcej o architekturze Docker można uzyskać, odczytując [omówienie Docker](https://docs.docker.com/engine/understanding-docker/) w witrynie Docker. 

Przenoszenie aplikacji konsoli jest wykonanie kilku kroków.

1. [Tworzenie aplikacji](#building-the-application)
1. [Tworzenie plik Dockerfile obrazu](#creating-the-dockerfile)
1. [Proces, aby skompilować i uruchomić kontenera Docker](#creating-the-image)

## <a name="prerequisites"></a>Wymagania wstępne
Kontenery systemu Windows są obsługiwane w [systemu Windows 10 Anniversary aktualizacji](https://www.microsoft.com/en-us/software-download/windows10/) lub [systemu Windows Server 2016](https://www.microsoft.com/en-us/cloud-platform/windows-server).

> [!NOTE]
>Jeśli używasz systemu Windows Server 2016, należy włączyć kontenery ręcznie ponieważ Instalator Docker dla systemu Windows nie włączy tę funkcję. Upewnij się, że wszystkie aktualizacje uruchomiono dla systemu operacyjnego, a następnie postępuj zgodnie z instrukcjami [wdrażania hosta kontenera](https://msdn.microsoft.com/virtualization/windowscontainers/deployment/deployment) artykuł, aby zainstalować kontenery i funkcje Docker.

Musisz mieć Docker dla systemu Windows, wersja 1.12 26 lub nowszej wersji Beta do obsługi systemu Windows kontenerów. Domyślnie Docker umożliwia kontenery opartymi na systemie Linux; Przełącz się do kontenerów systemu Windows przez kliknięcie prawym przyciskiem myszy ikonę Docker na pasku zadań i wybierz **przełączyć się do systemu Windows kontenery**. Docker uruchomi proces zmiany i może być wymagane ponowne uruchomienie.

![Windows-Containers](./media/console/SwitchContainer.png)

## <a name="building-the-application"></a>Tworzenie aplikacji
Zwykle aplikacje konsoli są dystrybuowane za pomocą Instalatora, FTP lub udziału plików wdrożenia. W przypadku wdrażania w danym kontenerze, zasoby muszą być skompilowane i przygotowane do lokalizacji, która może być używana podczas tworzenia obrazu Docker.

W *build.ps1*, skrypt używa [MSBuild](/visualstudio/msbuild/msbuild) skompilować aplikację, aby ukończyć zadanie tworzenia zasoby. Istnieje kilka parametrów przekazanych do MSBuild, aby zakończyć wymagane zasoby. Nazwa pliku projektu lub rozwiązania do skompilowania, lokalizacja dane wyjściowe, i na koniec konfiguracji (debugowania lub wersji).

W wywołaniu `Invoke-MSBuild` `OutputPath` ustawiono **publikowania** i `Configuration` ustawioną **wersji**. 

```
function Invoke-MSBuild ([string]$MSBuildPath, [string]$MSBuildParameters) {
    Invoke-Expression "$MSBuildPath $MSBuildParameters"
}

Invoke-MSBuild -MSBuildPath "MSBuild.exe" -MSBuildParameters ".\ConsoleRandomAnswerGenerator.csproj /p:OutputPath=.\publish /p:Configuration=Release"
```

## <a name="creating-the-dockerfile"></a>Tworzenie plik Dockerfile
Obraz podstawowy używany dla konsoli aplikacji .NET Framework jest `microsoft/windowsservercore`, ogólnie dostępna w [Centrum Docker](https://hub.docker.com/r/microsoft/windowsservercore/). Obraz podstawowy zawiera minimalnej instalacji systemu Windows Server 2016, .NET Framework 4.6.2 i służy jako podstawowy obraz systemu operacyjnego Windows kontenerów.

```
FROM microsoft/windowsservercore
ADD publish/ /
ENTRYPOINT ConsoleRandomAnswerGenerator.exe
```
W pierwszym wierszu plik Dockerfile wyznacza przy użyciu obrazu podstawowego [ `FROM` ](https://docs.docker.com/engine/reference/builder/#/from) instrukcji. Następnie [ `ADD` ](https://docs.docker.com/engine/reference/builder/#/add) w pliku kopiuje zasoby aplikacji z **publikowania** folderu do folderu głównego kontenera i ostatnich; ustawienie [ `ENTRYPOINT` ](https://docs.docker.com/engine/reference/builder/#/entrypoint) stanów obrazu jest tego polecenia lub aplikacji, które zostanie uruchomione po uruchomieniu kontenera. 

## <a name="creating-the-image"></a>Tworzenie obrazu
Aby utworzyć obraz Docker, następujący kod został dodany do *build.ps1* skryptu. Po uruchomieniu skryptu `console-random-answer-generator` obraz został utworzony za pomocą zasoby skompilowana z MSBuild zdefiniowane w [tworzenie aplikacji](#building-the-application) sekcji.

```powershell
$ImageName="console-random-answer-generator"

function Invoke-Docker-Build ([string]$ImageName, [string]$ImagePath, [string]$DockerBuildArgs = "") {
    echo "docker build -t $ImageName $ImagePath $DockerBuildArgs"
    Invoke-Expression "docker build -t $ImageName $ImagePath $DockerBuildArgs"
}

Invoke-Docker-Build -ImageName $ImageName -ImagePath "."
```

Uruchom przy użyciu skryptu `.\build.ps1` w wierszu polecenia programu PowerShell.

Po zakończeniu kompilacji przy użyciu `docker images` polecenie z wiersza polecenia lub w wierszu polecenia programu PowerShell; zobaczysz, że obraz został utworzony i gotowych do uruchomienia.

```
REPOSITORY                        TAG                 IMAGE ID            CREATED             SIZE
console-random-answer-generator   latest              8f7c807db1b5        8 seconds ago       7.33 GB
```

## <a name="running-the-container"></a>Uruchomione w kontenerze
Kontener można uruchomić z wiersza polecenia, używając polecenia Docker.

```
docker run console-random-answer-generator "Are you a square container?"
```

Dane wyjściowe

```
The answer to your question: 'Are you a square container?' is Concentrate and ask again on (70C3D48F4343)
```

Po uruchomieniu `docker ps -a` poleceń w programie PowerShell, widać, że kontener nadal istnieje.

```
CONTAINER ID        IMAGE                             COMMAND                  CREATED             STATUS                          
70c3d48f4343        console-random-answer-generator   "cmd /S /C ConsoleRan"   2 minutes ago       Exited (0) About a minute ago      
```

W kolumnie Stan wynika, że na "około minutę temu", jest kompletna aplikacja i może zostać zamknięty. Jeśli polecenie zostało uruchomione kilkaset razy, byłoby STU kontenery static po lewej stronie z bezczynne. W scenariuszu początku idealne operacja zakończyła się w pracy i zamknięcie lub czyszczenia. Aby osiągnąć ten przepływ pracy, dodawanie `--rm` opcji w celu `docker run` polecenia spowoduje usunięcie kontenera natychmiast `Exited` odebraniu sygnału.

```
docker run --rm console-random-answer-generator "Are you a square container?"
```

Uruchomienie polecenia przy użyciu tej opcji, a następnie sprawdzając w danych wyjściowych `docker ps -a` polecenie; Zwróć uwagę, że identyfikator kontenera ( `Environment.MachineName`) nie jest na liście.

### <a name="running-the-container-using-powershell"></a>Uruchomiona kontenera przy użyciu programu PowerShell
W przykładowych plików projektu jest również *run.ps1* czyli przykładowy sposób do uruchamiania aplikacji akceptować argumenty przy użyciu programu PowerShell.

Aby uruchomić, Otwórz program PowerShell i użyj następującego polecenia:

```
.\run.ps1 "Is this easy or what?"
```

## <a name="summary"></a>Podsumowanie
Wystarczy dodać plik Dockerfile i publikowanie aplikacji, containerize aplikacji konsoli .NET Framework i teraz korzystać z uruchamiając wiele wystąpień, czystego uruchomienia i zatrzymania i więcej możliwości systemu Windows Server 2016 bez żadnego na wszystkich zmian w kodzie aplikacji.
