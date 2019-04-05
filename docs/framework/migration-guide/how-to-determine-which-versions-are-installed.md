---
title: 'Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.'
ms.date: 04/02/2019
dev_langs:
- csharp
- vb
ms.custom: updateeachrelease
helpviewer_keywords:
- versions, determining for .NET Framework
- .NET Framework, determining version
ms.assetid: 40a67826-e4df-4f59-a651-d9eb0fdc755d
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 570cbd49fd8a8ea42d1c43ebe067a0d2d3f9dc27
ms.sourcegitcommit: 68eb5c4928e2b082f178a42c16f73fedf52c2ab8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/05/2019
ms.locfileid: "59055238"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.

Użytkownicy mogą [zainstalować](https://docs.microsoft.com/dotnet/framework/install) i uruchamiania wielu wersji programu .NET Framework na swoich komputerach. Podczas tworzenia lub wdrażania aplikacji, może być konieczne wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika. 

.NET Framework składa się z dwóch głównych składników, które są określane oddzielnie:  
  
- Zbiór zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji. .NET Framework i zestawy współużytkują ten sam numer wersji.  
  
- Środowisko uruchomieniowe języka wspólnego (CLR) zarządza, która wykonuje kod w swojej aplikacji. Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).  

> [!NOTE]
> Każda nowa wersja programu .NET Framework zachowuje funkcje z poprzednich wersji i dodaje nowe funkcje. W tym samym czasie, co oznacza, że bez konieczności odinstalowywania poprzednich wersji można zainstalować środowiska .NET Framework, można załadować wiele wersji programu .NET Framework na pojedynczym komputerze. Ogólnie rzecz biorąc nie należy odinstalować poprzednie wersje programu .NET Framework, ponieważ aplikacja może zależeć od określonej wersji i mogą przestać działać, jeśli ta wersja została usunięta.
>
> Istnieje następująca różnica między wersją .NET Framework i wersji środowiska CLR: 
> - Wersja .NET Framework jest oparta na zbiór zestawów, które tworzą biblioteki klas .NET Framework. Na przykład .NET Framework w wersji obejmują 4.5, 4.6.1 i 4.7.2. 
>- Wersja środowiska CLR jest oparty na środowiska uruchomieniowego, w którym wykonywane aplikacji programu .NET Framework. Jednej wersji środowiska CLR zazwyczaj obsługuje wiele wersji .NET Framework. Na przykład środowisko CLR w wersji 4.0.30319. *xxxxx* obsługuje wersje programu .NET Framework 4 za pośrednictwem 4.5.2 i wersji środowiska CLR 4.0.30319.42000 obsługuje wersje programu .NET Framework, począwszy od programu .NET Framework 4.6. 
>
> Aby uzyskać więcej informacji na temat wersji, zobacz [wersje programu .NET Framework i zależności](versions-and-dependencies.md).


Aby uzyskać listę wersji programu .NET Framework zainstalowana na komputerze, możesz uzyskać dostępu do rejestru. Można albo użyj Edytora rejestru, aby wyświetlić rejestr lub wykonuje zapytania za pomocą kodu:
 
- Znajdź nowszej wersji programu .NET Framework (4.5 i nowsze): 
     - [Użyj Edytora rejestru, aby znaleźć wersji programu .NET Framework](#net_b)  
     - [Wykonaj zapytanie dotyczące rejestru dla wersji programu .NET Framework przy użyciu kodu](#net_d)  
     - [Wykonaj zapytanie dotyczące rejestru dla wersji programu .NET Framework za pomocą programu PowerShell](#ps_a)
- Znajdź starsze wersje programu .NET Framework (1&#8211;4):
     - [Użyj Edytora rejestru, aby znaleźć wersji programu .NET Framework](#net_a)
     - [Wykonaj zapytanie dotyczące rejestru dla wersji programu .NET Framework przy użyciu kodu](#net_c)   

Aby uzyskać listę wersji środowiska CLR, zainstalowane na komputerze, użyj narzędzia lub kodu:  
  
- [Użyj narzędzia Clrver](#clr_a)  
- [Tworzenie zapytania klasę Environment przy użyciu kodu](#clr_b)  

Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji programu .NET Framework, zobacz [jak: Określanie, które aktualizacje programu .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md). 
  

## <a name="find-newer-net-framework-versions-45-and-later"></a>Znajdź nowszej wersji programu .NET Framework (4.5 i nowsze)

<a name="net_b"></a> 
### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Znajdź wersje programu .NET Framework 4.5 i nowsze w rejestrze

1. Z **Start** menu, wybierz **Uruchom**, wprowadź *regedit*, a następnie wybierz pozycję **OK**.

     Musi mieć poświadczenia administracyjne, aby uruchomić program regedit.

2. W Edytorze rejestru otwórz następujący podklucz: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full**. Jeśli **pełne** podklucz nie będą dostępne, a następnie nie ma programu .NET Framework 4.5 lub nowszy.

    > [!NOTE]
    > **NET Framework Setup** folder w rejestrze nie *nie* rozpoczyna się kropką.

3. Sprawdź, czy wpis typu DWORD o nazwie **wersji**. Jeśli istnieje, musisz .NET Framework 4.5 lub nowszy zainstalowany. Jego wartość to klucz wersji, który odnosi się do określonej wersji programu .NET Framework. Na poniższej ilustracji, na przykład, wartość **wersji** wpis jest *378389*, czyli na klucz wersji .NET Framework 4.5. 

     ![Wpis rejestru dla programu .NET Framework 4.5](media/clr-installdir.png "wpis rejestru dla programu .NET Framework 4.5")

W poniższej tabeli wymieniono wartości **wersji** DWORD w poszczególnych systemach operacyjnych .NET Framework 4.5 i nowsze wersje.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|Wersja programu .NET Framework|Wartość DWORD dotycząca wersji|
|--------------------------------|-------------|
|.NET Framework 4.5|Wszystkie systemy operacyjne Windows: 378389|
|.NET Framework 4.5.1|Windows 8.1 i Windows Server 2012 R2: 378675<br />Na wszystkich innych Windows systemów operacyjnych: 378758|
|.NET Framework 4.5.2|Wszystkie systemy operacyjne Windows: 379893|
|.NET Framework 4.6|W systemie Windows 10: 393295<br />Na wszystkich innych Windows systemów operacyjnych: 393297|
|.NET Framework 4.6.1|W systemach Windows 10 listopada Update: 394254<br />Na wszystkich innych Windows systemów (w tym Windows 10): 394271|
|.NET Framework 4.6.2|W Rocznicowej aktualizacji systemu Windows 10 i Windows Server 2016: 394802<br />Na wszystkich innych Windows systemów (łącznie z innymi systemami operacyjnymi Windows 10): 394806|
|.NET framework 4.7|W systemie Windows 10 dla kreatywnych: 460798<br />Na wszystkich innych Windows systemów (łącznie z innymi systemami operacyjnymi Windows 10): 460805| 
|.NET Framework 4.7.1|W Windows 10 Fall Creators Update i Windows Server w wersji 1709. 461308<br/>Na wszystkich innych Windows systemów (łącznie z innymi systemami operacyjnymi Windows 10): 461310|
|.NET Framework 4.7.2|W systemie Windows 10 kwietnia 2018 Update i Windows Server w wersji 1803: 461808<br/>We wszystkich systemach operacyjnych Windows innych niż Windows 10 kwietnia 2018 Update i Windows Server w wersji 1803: 461814|  

Można użyć tych wartości w następujący sposób:

- Aby ustalić, czy określonej wersji programu .NET Framework jest zainstalowana na konkretnej wersji systemu operacyjnego Windows, należy przetestować czy **wersji** jest wartość DWORD *równa* wartości na liście Tabela. Na przykład, aby ustalić, czy program .NET Framework 4.6 jest obecny w systemie Windows 10, testowania **wersji** wartość, która jest *równa* 393295.

- Aby określić, czy minimalną wersję systemu .NET Framework jest obecny, należy użyć mniejszego **wersji** wartość DWORD dla danej wersji. Na przykład, jeśli aplikacja działa w ramach platformy .NET Framework 4.6 lub nowszej wersji, testowania **wersji** wartość DWORD *większa lub równa* 393295. Aby uzyskać tabelę, która zawiera tylko minimalne **wersji** wartość DWORD dla każdej wersji systemu .NET Framework, zobacz [minimalnej wartości DWORD wersji .NET Framework 4.5 i nowsze wersje](minimum-release-dword.md).

- Aby przetestować dla różnych wersji, najpierw testowanie pod kątem wartość, która jest *większa lub równa* mniejsze wartości DWORD wartości dla najnowszej wersji .NET Framework, a następnie porównanie wartości z mniejszą wartość DWORD dla każdego kolejnych starszej wersji. Na przykład, jeśli aplikacja wymaga programu .NET Framework w wersji 4.7 lub nowszej, a użytkownik chce ustalenie określonej wersji programu .NET Framework jest obecny, Rozpocznij od testowanie pod kątem **wersji** wartość DWORD *większy niż lub równe*  do 461808 (mniejszą wartość DWORD na platformie .NET 4.7.2). Następnie porównaj **wersji** wartość DWORD o mniejszej wartości każdego nowszej wersji .NET Framework. Aby uzyskać tabelę, która zawiera tylko minimalne **wersji** wartość DWORD dla każdej wersji systemu .NET Framework, zobacz [minimalnej wartości DWORD wersji .NET Framework 4.5 i nowsze wersje](minimum-release-dword.md).

<a name="net_d"></a> 
### <a name="find-net-framework-versions-45-and-later-with-code"></a>Znajdź wersje programu .NET Framework 4.5 lub nowszy z kodem

1. Użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metod w celu uzyskania dostępu do **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework setup\ndp\v4\full ma** podkluczy w rejestrze systemu Windows.

    Istnienie **wersji** wpis DWORD w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework setup\ndp\v4\full ma** podklucz wskazuje na to, że jest .NET Framework 4.5 lub nowszej wersji. zainstalowana na komputerze. 

2. Sprawdź wartość **wersji** wpis, aby ustalić zainstalowaną wersję. Być zgodne, sprawdź, czy wartość większą niż lub równa wartości na liście [tabeli wersji .NET Framework](#version_table).

Poniższy przykład sprawdza wartość **wersji** wpis w rejestrze, aby znaleźć .NET Framework 4.5 i nowsze wersje, które są zainstalowane:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

W tym przykładzie następuje zalecana praktyka dla kontroli wersji:

- Sprawdza, czy wartość **wersji** wpis jest *większa lub równa* wartości kluczy znanych wydania.

- Sprawdza w kolejności od najbardziej aktualną wersję do najwcześniejszej wersji.

<a name="ps_a"></a> 
### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Sprawdź, czy są wymagane co najmniej .NET Framework w wersji (4.5 lub nowszy) za pomocą programu PowerShell

- Użyj poleceń programu PowerShell, aby sprawdzić wartość **wersji** wpisu **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework setup\ndp\v4\full ma** podklucza.

Poniższe przykłady należy sprawdzić wartość **wersji** wpis, aby określić, czy programu .NET Framework 4.6.2 lub nowszy jest zainstalowany. Ten kod zwraca `True` Jeśli jest zainstalowany i `False` inaczej.

```PowerShell
# PowerShell 5
 Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' |  Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
 ```

```PowerShell
# PowerShell 4
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Aby sprawdzić, czy inny minimalna wymagana wersja programu .NET Framework, należy zastąpić *394802* w tych przykładach za pomocą **wersji** wartość z [tabeli wersji .NET Framework](#version_table).

## <a name="find-older-net-framework-versions-182114"></a>Znajdź starsze wersje programu .NET Framework (1&#8211;4)

<a name="net_a"></a>
### <a name="find-net-framework-versions-182114-in-the-registry"></a>Znajdź .NET Framework w wersji 1&#8211;4 w rejestrze 
  
1. Z **Start** menu, wybierz **Uruchom**, wprowadź *regedit*, a następnie wybierz pozycję **OK**.
  
    Musi mieć poświadczenia administracyjne, aby uruchomić program regedit.  

2. W Edytorze rejestru otwórz następujący podklucz: **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP**:  

    - Dla wersji programu .NET Framework 1.1 przez 3.5 każdej zainstalowanej wersji jest wymieniony jako podklucza w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP** podklucza. Na przykład **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v3.5**. Numer wersji jest przechowywany jako wartość podklucza wersji **wersji** wpisu. 
     
    - .NET Framework 4 **wersji** wpis znajduje się w **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client** podklucz **HKEY_LOCAL_MACHINE\SOFTWARE\ Microsoft\NET Framework Setup\NDP\v4.0\Full** podklucza, lub w obu tych podkluczach.

    > [!NOTE]
    > **NET Framework Setup** lokalizacji w rejestrze nie rozpoczyna się kropką.

    Na poniższej ilustracji przedstawiono podklucz i jego **wersji** wpis dla programu .NET Framework 3.5.

    ![Wpis rejestru dla programu .NET Framework 3.5. ](media/net-4-and-earlier.png ".NET framework 3.5 i wcześniejszymi wersjami")

<a name="net_c"></a> 
### <a name="find-net-framework-versions-182114-with-code"></a>Znajdź .NET Framework w wersji 1&#8211;4 przy użyciu kodu

- Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby uzyskać dostęp do **HKEY_LOCAL_MACHINE\Software\Microsoft\NET Framework Setup\NDP** podkluczy w rejestrze systemu Windows.

Poniższy przykład umożliwia znalezienie .NET Framework 1&#8211;wersji 4, które są zainstalowane:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]


## <a name="find-clr-versions"></a>Znajdź wersji środowiska CLR
  
<a name="clr_a"></a> 
### <a name="find-the-current-clr-version-with-clrverexe"></a>Znaleźć bieżącą wersję środowiska CLR przy użyciu Clrver.exe

Użyj [narzędzia wersji środowiska CLR (Clrver.exe)](../tools/clrver-exe-clr-version-tool.md) do określenia, które wersje środowiska CLR są instalowane na komputerze:

- Z [wiersz polecenia programisty dla programu Visual Studio](https://docs.microsoft.com/dotnet/framework/tools/developer-command-prompt-for-vs), wprowadź `clrver`.

    Przykładowe dane wyjściowe:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a> 
### <a name="find-the-current-clr-version-with-the-environment-class"></a>Znaleźć bieżącą wersję środowiska CLR przy użyciu klasy środowiska

> [!IMPORTANT]
> .NET Framework 4.5 i nowsze wersje, nie należy używać <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do wykrywania wersji środowiska CLR. Zamiast tego wykonaj zapytanie dotyczące rejestru zgodnie z opisem w [znaleźć .NET Framework w wersji 4.5 lub nowszy z kodem](#net_d).

1. Zapytanie <xref:System.Environment.Version?displayProperty=nameWithType> właściwość służąca do pobierania <xref:System.Version> obiektu. 

    Zwrócony `System.Version` obiektu określa wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.

    W przypadku wersji .NET Framework 4, 4.5, 4.5.1 i 4.5.2, reprezentacja ciągu zwracanego <xref:System.Version> obiekt ma postać 4.0.30319. *XXXXX*. Dla platformy .NET Framework 4.6 i nowszymi wersjami posiada 4.0.30319.42000 formularza.    

2. Po utworzeniu `Version` obiektów, badać je w następujący sposób:

   - Dla głównej wersji identyfikator (na przykład *4* w wersji 4.0), użyj <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości.

   - Dla osób nieletnich wersji identyfikator (na przykład *0* w wersji 4.0), użyj <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości.

   - Aby uzyskać całą wersję ciągu (na przykład *4.0.30319.18010*), użyj <xref:System.Version.ToString%2A?displayProperty=nameWithType> metody. Ta metoda zwraca pojedynczą wartość odzwierciedlającą wersję środowiska uruchomieniowego, które wykonuje kod. Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.



W poniższym przykładzie użyto <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość służąca do pobierania informacji o wersji środowiska CLR:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie, które aktualizacje programu .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalowanie programu .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [Wersje programu .NET framework i zależności](versions-and-dependencies.md)
