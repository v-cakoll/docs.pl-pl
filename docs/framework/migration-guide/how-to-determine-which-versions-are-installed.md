---
title: 'Porady: Określanie, które wersje programu .NET Framework są zainstalowane'
ms.date: 01/24/2018
ms.prod: .net-framework
ms.technology:
- dotnet-clr
ms.topic: article
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
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: edf1e5a53f6f578f943cf8775a798b5681d2d9dd
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Porady: Określanie, które wersje programu .NET Framework są zainstalowane

Użytkownicy mogą zainstalować i uruchamiać wiele wersji .NET Framework na swoich komputerach. Podczas opracowywania lub wdrożyć aplikację, konieczne może być wiedzieć, które wersje programu .NET Framework są zainstalowane na komputerze użytkownika. Należy pamiętać, że programu .NET Framework składa się z dwóch głównych elementów, które numerów wersji oddzielnie:  
  
-   Zbiór zestawów, które są kolekcjami typów i zasobów, które zapewniają funkcje dla aplikacji. .NET Framework i zestawy udostępnianie tego samego numeru wersji.  
  
-   Środowisko uruchomieniowe języka wspólnego (CLR), która zarządza i wykonuje kod aplikacji. Środowisko CLR jest identyfikowany przez numer wersji (zobacz [wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)).  
  
 Aby uzyskać dokładne listę zainstalowanych na komputerze wersji .NET Framework, można wyświetlić rejestru lub zapytanie dotyczące rejestru w kodzie:  
  
 [Wyświetlanie w rejestrze (wersje 1-4)](#net_a)  
 [Wyświetlanie w rejestrze (w wersji 4.5 lub nowszy)](#net_b)  
 [Zapytanie dotyczące rejestru (wersje 1-4) za pomocą kodu](#net_c)  
 [Zapytanie dotyczące rejestru (w wersji 4.5 lub nowszej) za pomocą kodu](#net_d)  
 [Zapytanie dotyczące rejestru (w wersji 4.5 lub nowszej) przy użyciu programu PowerShell](#ps_a)  
  
 Aby znaleźć wersji środowiska CLR, można użyć narzędzia lub kodu:  
  
 [Za pomocą narzędzia Clrver](#clr_a)  
 [Do klasy System.Environment zapytania przy użyciu kodu](#clr_b)  
  
 Uzyskać informacji o wykrywaniu zainstalowanych aktualizacji dla każdej wersji systemu .NET Framework, zobacz [porady: ustalić, które .NET Framework aktualizacje są instalowane](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md). Aby uzyskać informacje na temat Instalowanie programu .NET Framework, zobacz [Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md).  
  
<a name="net_a"></a>   
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-1-4"></a>Aby znaleźć wersje programu .NET Framework, wyświetlając rejestru (.NET Framework 1-4)  
  
1.  Na **Start** menu, wybierz **Uruchom**.  
  
2.  W **Otwórz** wprowadź **regedit.exe**.  
  
     Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.  
  
3.  W Edytorze rejestru otwórz następujący podklucz:  
  
     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP`  
  
     Zainstalowane wersje są wymienione w podkluczu NDP. Numer wersji jest zapisany w **wersji** wpisu. Dla [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] **wersji** wpis podlega klienta lub pełne podklucz (w obszarze NPR) lub w obu podkluczach.  
  

    > [!NOTE]
    > Folder „NET Framework Setup” w rejestrze nie rozpoczyna się kropką.

<a name="net_b"></a> 
## <a name="to-find-net-framework-versions-by-viewing-the-registry-net-framework-45-and-later"></a>Aby znaleźć wersje programu .NET Framework, wyświetlając rejestru (.NET Framework 4.5 lub nowszy)

1. Na **Start** menu, wybierz **Uruchom**.

2. W **Otwórz** wprowadź **regedit.exe**.

     Musisz mieć poświadczenia administracyjne, aby uruchomić program regedit.exe.

3. W Edytorze rejestru otwórz następujący podklucz:

     `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full`

     Należy pamiętać, że ścieżka do `Full` podklucz zawiera podklucz `Net Framework` zamiast `.NET Framework`.

    > [!NOTE]
    > Jeśli `Full` podklucz nie jest obecny, a następnie nie ma programu .NET Framework 4.5 lub nowszej.

     Sprawdź, czy wartość DWORD o nazwie `Release`. Istnienie `Release` DWORD wskazuje, że [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszej został zainstalowany na tym komputerze.

     ![Wpis rejestru dla programu .NET Framework 4.5. ] (../../../docs/framework/migration-guide/media/clr-installdir.png "CLR_InstallDir")

     Wartość `Release` DWORD wskazuje, która wersja architektury .NET Framework jest zainstalowana.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Wartość DWORD dotycząca wersji|Wersja|
    |--------------------------------|-------------|
    |378389|.NET Framework 4.5|
    |378675|.NET framework 4.5.1 zainstalowaną w systemie Windows 8.1 lub Windows Server 2012 R2|
    |378758|.NET framework 4.5.1 w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2|
    |379893|.NET Framework 4.5.2|
    |W systemach Windows 10: 393295<br /><br /> We wszystkich wersjach systemu operacyjnego: 393297|[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|
    |W systemach Windows 10 listopada Update: 394254<br /><br /> We wszystkich wersjach systemu operacyjnego: 394271|[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|
    |W usłudze Windows 10 Anniversary Update: 394802<br /><br /> We wszystkich wersjach systemu operacyjnego: 394806|[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]| 
    |Na 10 twórców usługi Windows Update: 460798<br/><br/> We wszystkich wersjach systemu operacyjnego: 460805 | .NET framework 4.7 |
    |W systemie Windows 10 można podzielić aktualizacji twórcy: 461308<br/><br/> We wszystkich wersjach systemu operacyjnego: 461310 | .NET Framework 4.7.1 |
    
<a name="net_c"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-1-4"></a>Aby znaleźć wersje programu .NET Framework, badając rejestru w kodzie (.NET Framework 1-4)

- Użyj <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy do podklucza Software\Microsoft\NET Framework Setup\NDP\ w HKEY_LOCAL_MACHINE w rejestrze systemu Windows.

     Poniższy kod przedstawia przykład tego zapytania.

    > [!NOTE]
    > Ten kod nie przedstawiają sposób wykrywania [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszym. Sprawdź `Release` DWORD, aby wykryć te wersje, zgodnie z opisem w poprzedniej sekcji. Dla kodu, które wykrywają [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowszych wersjach, zobacz następną sekcję w tym artykule.

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

     W przykładzie są generowane dane wyjściowe podobne do następujących:

    ```
    v2.0.50727  2.0.50727.4016  SP2
    v3.0  3.0.30729.4037  SP2
    v3.5  3.5.30729.01  SP1
    v4
      Client  4.0.30319
      Full  4.0.30319
    ```

<a name="net_d"></a> 
## <a name="to-find-net-framework-versions-by-querying-the-registry-in-code-net-framework-45-and-later"></a>Aby znaleźć wersje programu .NET Framework, badając rejestru w kodzie (.NET Framework 4.5 lub nowszy)

1. Istnienie `Release` DWORD wskazuje, że na komputerze zainstalowano .NET Framework 4.5 lub nowszej. Wartość słowa kluczowego wskazuje zainstalowanej wersji. Aby sprawdzić to słowo kluczowe, użyj <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A> metody <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType> klasy do podklucza Software\Microsoft\NET Framework Setup\NDP\v4\Full w HKEY_LOCAL_MACHINE w rejestrze systemu Windows.

2. Sprawdź wartość `Release` — słowo kluczowe, aby określić zainstalowaną wersję. Być zgodne z nowszymi, można sprawdzić wartość większa niż lub równa wartości wymienionych w tabeli. Poniżej przedstawiono wersje programu .NET Framework i skojarzone `Release` słów kluczowych.

    [!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

    |Wersja|Wartość DWORD dotycząca wersji|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET framework 4.5.1 zainstalowane z Windows 8.1|378675|
    |.NET framework 4.5.1 w systemie Windows 8, Windows 7 z dodatkiem SP1 lub Windows Vista z dodatkiem SP2|378758|
    |.NET Framework 4.5.2|379893|
    |.NET framework 4.6 zainstalowanego z systemem Windows 10|393295|
    |.NET framework 4.6 zainstalowane we wszystkich wersjach systemu operacyjnego Windows|393297|
    |.NET framework 4.6.1, systemie Windows 10|394254|
    |.NET framework 4.6.1 zainstalowane we wszystkich wersjach systemu operacyjnego Windows|394271|
    |.NET framework 4.6.2 z zainstalowanym systemem Windows 10 Anniversary aktualizacji|394802|
    |.NET framework 4.6.2 zainstalowane we wszystkich wersjach systemu operacyjnego Windows|394806|
    |4.7 framework .NET zainstalowany w systemie Windows 10 twórców Update|460798|
    |4.7 framework .NET zainstalowany w innych wersjach systemu operacyjnego Windows|460805|
    |.NET framework w systemie Windows 10 spadek twórców Update 4.7.1|461308|
    |.NET framework 4.7.1 zainstalowane we wszystkich wersjach systemu operacyjnego Windows|461310|

     Następujące testy przykład `Release` wartości rejestru w celu ustalenia, czy [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] lub nowsza wersja programu .NET Framework jest zainstalowana.

     [!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
     [!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

     W tym przykładzie zalecaną praktyką w kontroli wersji są następujące:

    - Sprawdza, czy wartość `Release` wpis jest *większa niż lub równa* wartości kluczy znane wersji.

    - Sprawdza w celu najstarszą wersję z najnowszej wersji.

<a name="ps_a"></a> 
## <a name="to-check-for-a-minimum-required-net-framework-version-by-querying-the-registry-in-powershell-net-framework-45-and-later"></a>Aby sprawdzić minimalna wymagana wersja programu .NET Framework, badając rejestru w programie PowerShell (.NET Framework 4.5 lub nowszy)

- Poniższy przykład sprawdza wartość `Release` — słowo kluczowe, aby określić, czy .NET Framework 4.6.2 lub nowszy jest zainstalowany, niezależnie od wersji systemu operacyjnego (zwracanie `True` Jeśli jest i `False` w przeciwnym razie).

    ```PowerShell
    Get-ChildItem "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full\" | Get-ItemPropertyValue -Name Release | ForEach-Object { $_ -ge 394802 } 
    ```

    Można zastąpić `394802` w poprzednim przykładzie z innej wartości z poniższej tabeli, aby wyszukać inny minimalna wymagana wersja programu .NET Framework.
  
    |Wersja|Minimalna wartość DWORD zlecenia|
    |-------------|--------------------------------|
    |.NET Framework 4.5|378389|
    |.NET Framework 4.5.1|378675|
    |.NET Framework 4.5.2|379893|
    |[!INCLUDE[net_v46](../../../includes/net-v46-md.md)]|393295|
    |[!INCLUDE[net_v461](../../../includes/net-v461-md.md)]|394254|
    |[!INCLUDE[net_v462](../../../includes/net-v462-md.md)]|394802|
    |.NET framework 4.7|460798|
    |.NET Framework 4.7.1|461308|
    
<a name="clr_a"></a> 
## <a name="to-find-the-current-runtime-version-by-using-the-clrver-tool"></a>Aby znaleźć bieżącą wersję środowiska uruchomieniowego za pomocą narzędzia Clrver

- Użyj narzędzia wersji środowiska CLR (Clrver.exe) w celu ustalenia, które wersje środowiska uruchomieniowego języka wspólnego są zainstalowane na komputerze.

     Z programu Visual Studio wiersz polecenia, wprowadź `clrver`. To polecenie tworzy dane wyjściowe podobne do poniższych:

    ```
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

     Aby uzyskać więcej informacji na temat stosowania tego narzędzia, zobacz [Clrver.exe (narzędzie wersji środowiska CLR)](~/docs/framework/tools/clrver-exe-clr-version-tool.md).

<a name="clr_b"></a> 
## <a name="to-find-the-current-runtime-version-by-querying-the-environment-class-in-code"></a>Aby znaleźć bieżącą wersję środowiska uruchomieniowego, badając klasę Environment w kodzie

- Zapytanie <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości do pobrania <xref:System.Version> obiekt, który identyfikuje wersję środowiska uruchomieniowego, który jest aktualnie wykonywany kod. Można użyć <xref:System.Version.Major%2A?displayProperty=nameWithType> właściwości można pobrać identyfikatora wydaniem (na przykład "4" w wersji 4.0), <xref:System.Version.Minor%2A?displayProperty=nameWithType> właściwości, aby określić identyfikator wersji pomocniczej (na przykład "0" w wersji 4.0), lub <xref:System.Object.ToString%2A?displayProperty=nameWithType> metodę, aby pobrać całej wersji ciąg (na przykład "4.0.30319.18010", jak pokazano w poniższym kodzie). Ta właściwość zwraca jedną wartość odzwierciedlającą wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Właściwość nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.

     Dla wersji .NET Framework 4, 4.5.1, 4.5 i 4.5.2 <xref:System.Environment.Version%2A?displayProperty=nameWithType> zwraca <xref:System.Version> obiektu, którego reprezentacji ciągu ma postać `4.0.30319.xxxxx`. Dla programu .NET Framework 4.6 i nowszych, składa się z formularza `4.0.30319.42000`.

    > [!IMPORTANT]
    > Dla [!INCLUDE[net_v45](../../../includes/net-v45-md.md)] i później, nie zaleca się przy użyciu <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwość, aby wykryć wersji środowiska uruchomieniowego. Zamiast tego, firma Microsoft zaleca, aby zbadać rejestru, zgodnie z opisem w [można znaleźć wersji systemu .NET Framework, badając rejestru w kodzie (.NET Framework 4.5 lub nowszej)](#net_d) wcześniej w tym artykule.

     Oto przykład kwerendy <xref:System.Environment.Version%2A?displayProperty=nameWithType> właściwości, aby uzyskać informacje o wersji środowiska uruchomieniowego:

     [!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
     [!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

     W przykładzie są generowane dane wyjściowe podobne do następujących:

    ```
    Version: 4.0.30319.18010
    ```

## <a name="see-also"></a>Zobacz także

[Instrukcje: określanie, które aktualizacje programu .NET Framework są zainstalowane](~/docs/framework/migration-guide/how-to-determine-which-net-framework-updates-are-installed.md)  
[Zainstaluj program .NET Framework dla deweloperów](../../../docs/framework/install/guide-for-developers.md)  
[Wersje i zależności](~/docs/framework/migration-guide/versions-and-dependencies.md)  
