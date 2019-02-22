---
title: 'Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.'
ms.date: 02/20/2019
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
ms.openlocfilehash: d7661b3ebaa8f29d6d3b2adbc56c405c8f0945f3
ms.sourcegitcommit: 07c4368273b446555cb2c85397ea266b39d5fe50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2019
ms.locfileid: "56584177"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Instrukcje: Określanie, które wersje programu .NET Framework są zainstalowane.

Użytkownicy mogą zainstalować i uruchamiać wiele wersji .NET Framework na swoich komputerach. Podczas tworzenia lub wdrażania aplikacji, może być konieczne wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika. Należy zwrócić uwagę na to, że .NET Framework składa się z dwóch głównych składników, które są określane oddzielnie:  
  
- Zbiór zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji. .NET Framework i zestawy współużytkują ten sam numer wersji.  
  
- Środowisko uruchomieniowe języka wspólnego (CLR) zarządza, która wykonuje kod w swojej aplikacji. Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
Aby uzyskać dokładne listę wersji programu .NET Framework zainstalowana na komputerze, można wyświetlić rejestr lub wykonaj zapytanie dotyczące rejestru w kodzie:  
  
 [Znajdź .NET Framework w wersji 1 – 4 w rejestrze](#net_a)  
 [Znajdź wersje programu .NET Framework 4.5 i nowsze w rejestrze)](#net_b)  
 [Wykonaj zapytanie dotyczące rejestru (wersje 1 – 4) za pomocą kodu](#net_c)  
 [Wykonaj zapytanie dotyczące rejestru (w wersji 4.5 lub nowszy) za pomocą kodu](#net_d)  
 [Przy użyciu programu PowerShell do wykonywania zapytań w rejestrze (w wersji 4.5 lub nowszy)](#ps_a)  

 Aby znaleźć wersję środowiska CLR, można użyć narzędzia lub kodu:  
  
 [Za pomocą narzędzia Clrver](#clr_a)  
 [Aby wysłać zapytanie klasy System.Environment przy użyciu kodu](#clr_b)  

> [!NOTE]
> Istnieje różnica między wersją .NET Framework i wspólne wersję środowiska uruchomieniowego języka (wspólnego CLR). Program .NET Framework jest wersjonowany na podstawie zestawu zestawów, które tworzą biblioteki klas programu .NET Framework. Na przykład .NET Framework w wersji obejmują 4.5, 4.6.1 i 4.7.2. Środowisko CLR jest określonej wersji środowiska uruchomieniowego programu .NET Framework aplikacje są wykonywane w oparciu i jednej wersji środowiska CLR zazwyczaj obsługuje wiele wersji .NET Framework. Środowisko CLR w wersji 4.30319. *xxxxx* obsługuje wersje programu .NET Framework 4, za pośrednictwem 4.5.2; Środowisko CLR w wersji 4.30319.42000 obsługuje wersje programu .NET Framework, począwszy od programu .NET Framework 4.6. Aby uzyskać więcej informacji, zobacz <xref:System.Environment.Version?displayProperty=nameWithType> właściwości.

 Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji programu .NET Framework, zobacz [jak: Określanie, które aktualizacje programu .NET Framework są zainstalowane](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Aby uzyskać informacje o instalowaniu programu .NET Framework, zobacz [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="find-net-framework-versions-1-4-in-the-registry"></a>Znajdź .NET Framework w wersji 1 – 4 w rejestrze 
  
1.  Na **Start** menu, wybierz **Uruchom**.  
  
2.  W **Otwórz** wprowadź **regedit.exe**.  
  
     Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.  
  
3.  W Edytorze rejestru otwórz następujący podklucz:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Dla wersji programu .NET Framework 1.1 przez 3.5 zainstalowane wersje są wymienione jako podklucze należące do `NDP` podklucza. Numer wersji jest przechowywany w podkluczu wersji **wersji** wpisu. 
     
     .NET Framework 4 **wersji** wpis znajduje się w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Client` podklucz `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4.0\Full` podklucza, lub w obu tych podkluczach.

    > [!NOTE]
    > Folder „NET Framework Setup” w rejestrze nie rozpoczyna się kropką.

    Poniższa ilustracja pokazuje, że podklucz programu .NET Framework 3.5, wraz z jego **wersji** wpisu.

     ![Wpis rejestru dla programu .NET Framework 3.5. ](../../../docs/framework/migration-guide/media/net-4-and-earlier.png ".NET framework 4 i starszych wersji")

<a name="net_b"></a> 
## <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Znajdź wersje programu .NET Framework 4.5 i nowsze w rejestrze

1. Na **Start** menu, wybierz **Uruchom**.

2. W **Otwórz** wprowadź **regedit.exe**.

     Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.

3. W Edytorze rejestru otwórz następujący podklucz:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Należy pamiętać, że ścieżka do `Full` podklucz obejmuje podklucz `Net Framework` zamiast `.NET Framework`.

    > [!NOTE]
    > Jeśli `Full` podklucz nie jest obecny, a następnie nie ma programu .NET Framework 4.5 lub nowszej.

     Wyszukaj wartość DWORD o nazwie `Release`. Istnienie `Release` typu DWORD wskazuje, że zainstalowano .NET Framework 4.5 lub nowszej na tym komputerze. Jego wartość to klucz wersji, który odnosi się do określonej wersji programu .NET Framework. Na poniższej ilustracji, na przykład, wartość `Release` DWORD jest 378389, czyli na klucz wersji .NET Framework 4.5. 

     ![Wpis rejestru dla programu .NET Framework 4.5. ](../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

W poniższej tabeli przedstawiono minimalną wartość `Release` DWORD dla każdej wersji systemu .NET Framework. Można użyć tych wartości w następujący sposób:

- Aby ustalić, czy minimalna wersja architektury .NET Framework jest obecny, test czy `Release` wartość DWORD znaleziony w rejestrze jest *większa lub równa* wartości wymienione w tabeli. Na przykład jeśli aplikacja wymaga .NET Framework w wersji 4.7 lub nowszej, czy test dla wersji minimalnej wartości klucza 460798.

- Do testowania dla różnych wersji, zaczynają się od najnowszej wersji .NET Framework, a następnie przetestować każda kolejne starszej wersji.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

|Wersja programu .NET Framework|Wartość DWORD dotycząca wersji|
|--------------------------------|-------------|
|.NET Framework 4.5|378389|
|.NET Framework 4.5.1|378675|
|.NET Framework 4.5.2|379893|
|.NET Framework 4.6|393295|
|.NET Framework 4.6.1|394254|
|.NET Framework 4.6.2|394802|
|.NET framework 4.7|460798|
|.NET Framework 4.7.1|461308|
|.NET Framework 4.7.2|461808|

Aby uzyskać pełną tabelę klawiszy wersji dla programu .NET Framework dla określonej wersji systemu operacyjnego Windows, zobacz [kluczy wersji .NET Framework i wersji systemu operacyjnego Windows](release-keys-and-os-versions.md).

<a name="net_c"></a> 
## <a name="find-net-framework-versions-1-4-with-code"></a>Znajdź .NET Framework w wersji 1 do 4 z kodem

- Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy, aby uzyskać dostęp do `Software\Microsoft\NET Framework Setup\NDP\` podkluczy w obszarze `HKEY_LOCAL_MACHINE` gałęzi w rejestrze systemu Windows.

     Poniższy kod przedstawia przykład tego zapytania.

    > [!NOTE]
    > Ten kod nie pokazuje, jak wykrywać .NET Framework 4.5 lub nowszej. Sprawdź `Release` DWORD, aby wykryć te wersje, zgodnie z opisem w poprzedniej sekcji. Kod, który wykrywa .NET Framework 4.5 lub nowszej wersji zobacz sekcję dalej w tym artykule.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

<a name="net_d"></a> 
## <a name="find-net-framework-versions-45-and-later-with-code"></a>Znajdź wersje programu .NET Framework 4.5 lub nowszy z kodem

1. Istnienie `Release` DWORD w `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full` klucz wskazuje, że .NET Framework 4.5 lub nowszej jest zainstalowane na komputerze. Wartość słowa kluczowego wskazuje zainstalowanej wersji. Aby sprawdzić to słowo kluczowe, użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType> metodach dostępu podkluczu w rejestrze systemu Windows.

2. Sprawdź wartość `Release` słowo kluczowe, aby ustalić zainstalowaną wersję. Być zgodne, możesz sprawdzić wartość większa niż lub równa wartości wymienione w tabeli w [znaleźć .NET Framework w wersji 4.5 lub nowszy w rejestrze](#net_b) sekcji.

Następujące testy przykład `Release` wartości w rejestrze, aby ustalić, czy jest zainstalowany program .NET Framework 4.5 lub nowszej wersji.

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

W tym przykładzie następuje zalecana praktyka dla kontroli wersji:

- Sprawdza, czy wartość `Release` wpis jest *większa lub równa* wartości kluczy znanych wydania.

- Sprawdza w kolejności od najbardziej aktualną wersję do najwcześniejszej wersji.

<a name="ps_a"></a> 
## <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Sprawdź, czy minimalna wymagana .NET Framework w wersji (4.5 lub nowszy) za pomocą programu PowerShell

Poniższy przykład sprawdza wartość `Release` — słowo kluczowe, aby określić, czy platformy .NET Framework 4.6.2 lub nowszy jest zainstalowany (zwracanie `True` , gdy jest i `False` inaczej).

    ```PowerShell
    # PowerShell 5
    Get-ChildItem 'HKLM:\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\' | Get-ItemPropertyValue -Name Release | Foreach-Object { $_ -ge 394802 } 
    ```

    ```PowerShell
    # PowerShell 4
    (Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -gt 394802
    ```

    You can replace `394802` in the previous example with another value from the following table in the [Find .NET Framework versions 4.5 and later in the registry](#net_b) section to check for a different minimum required .NET Framework version.
  
<a name="clr_a"></a> 
## <a name="find-the-current-clr-version-with-clrverexe"></a>Znaleźć bieżącą wersję środowiska CLR przy użyciu Clrver.exe

Użyj narzędzia wersji środowiska CLR (Clrver.exe) w celu ustalenia, które wersje środowiska uruchomieniowego języka wspólnego są zainstalowane na komputerze.

Wprowadź w wierszu polecenia dla deweloperów programu Visual Studio, `clrver`. To polecenie tworzy dane wyjściowe podobne do poniższych:

```console
Versions installed on the machine:
v2.0.50727
v4.0.30319
```

Aby uzyskać więcej informacji dotyczących używania tego narzędzia, zobacz [Clrver.exe (narzędzie wersji środowiska CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="find-the-current-clr-version-with-the-environment-class"></a>Znaleźć bieżącą wersję środowiska CLR przy użyciu klasy środowiska

Można pobrać wartość <xref:System.Environment.Version?displayProperty=nameWithType> właściwość służąca do pobierania <xref:System.Version> obiektu, który identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Ta właściwość zwraca jedną wartość odzwierciedlającą wersję środowiska uruchomieniowego, które aktualnie wykonuje kod; nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze. Możesz użyć <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji głównej (na przykład "4" w wersji 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości, aby uzyskać identyfikator wersji pomocniczej (na przykład, "0" do wersji 4.0 lub nowszej), lub <xref:System.Version.ToString%2A?displayProperty=nameWithType> metodę, aby uzyskać całą wersję ciąg (na przykład "4.0.30319.18010", jak pokazano w poniższym kodzie). 

Dla platformy .NET Framework 4, 4.5, 4.5.1 i 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość zwraca <xref:System.Version> obiektu, którego reprezentacja ciągu ma postać `4.0.30319.xxxxx`. Dla programu .NET Framework 4.6 lub nowszy, ma on postać `4.0.30319.42000`.

> [!IMPORTANT]
> Dla programu .NET Framework 4.5 lub nowszy, zaleca się używania <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do wykrywania wersji środowiska uruchomieniowego. Zamiast tego zaleca się zapytania rejestru zgodnie z opisem w [można znaleźć wersji programu .NET Framework, wykonując zapytanie w rejestrze w kodzie (.NET Framework 4.5 i nowsze)](#net_d) sekcji we wcześniejszej części tego artykułu.

W poniższym przykładzie użyto <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość służąca do pobierania informacji o wersji środowiska uruchomieniowego:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie, które aktualizacje programu .NET Framework są zainstalowane.](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)
- [Instalowanie programu .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)
- [Wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)
