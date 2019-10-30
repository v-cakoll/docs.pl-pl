---
title: 'Instrukcje: Określanie, które wersje .NET Framework są zainstalowane'
ms.date: 04/18/2019
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
ms.openlocfilehash: fd2558d854986d3dc541a9adf3c15abd553ce2ea
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73039571"
---
# <a name="how-to-determine-which-net-framework-versions-are-installed"></a>Instrukcje: Określanie, które wersje .NET Framework są zainstalowane

Użytkownicy mogą [instalować](../install/index.md) i uruchamiać wiele wersji .NET Framework na swoich komputerach. Podczas opracowywania lub wdrażania aplikacji może być konieczne, aby wiedzieć, które wersje .NET Framework są zainstalowane na komputerze użytkownika.

.NET Framework składa się z dwóch głównych składników, które są osobno dla wersji:

- Zestaw zestawów, które są kolekcjami typów i zasobów zapewniających funkcje dla aplikacji. .NET Framework i zestawy mają ten sam numer wersji.

- Środowisko uruchomieniowe języka wspólnego (CLR), które zarządza kodem aplikacji i go wykonuje. Środowisko CLR jest identyfikowane za pomocą własnego numeru wersji (zobacz [wersje i zależności](versions-and-dependencies.md)).

> [!NOTE]
> Każda nowa wersja programu .NET Framework zachowuje funkcje z poprzednich wersji i dodaje nowe funkcje. Możesz ładować wiele wersji .NET Framework na jednym komputerze w tym samym czasie, co oznacza, że można zainstalować .NET Framework bez konieczności odinstalowywania poprzednich wersji. Ogólnie rzecz biorąc nie należy odinstalowywać poprzednich wersji .NET Framework, ponieważ używana aplikacja może zależeć od określonej wersji i może zostać przerwana, jeśli ta wersja zostanie usunięta.
>
> Istnieje różnica między wersją .NET Framework i wersją środowiska CLR:
>
> - Wersja .NET Framework jest oparta na zestawie zestawów, które tworzą bibliotekę klas .NET Framework. Na przykład .NET Framework wersje obejmują 4,5, 4.6.1 i 4.7.2.
> - Wersja środowiska CLR jest oparta na czasie wykonywania, w którym wykonywane są .NET Framework aplikacje. Jedna wersja środowiska CLR obsługuje zazwyczaj wiele wersji .NET Framework. Na przykład środowisko CLR w wersji 4.0.30319. *XXXXX* obsługuje .NET Framework wersje od 4 do 4.5.2, gdzie *XXXXX* jest mniejszy niż 42000, a środowisko CLR w wersji 4.0.30319.42000 obsługuje wersje .NET Framework, które zaczynają się od .NET Framework 4,6.
>
> Aby uzyskać więcej informacji na temat wersji, zobacz [.NET Framework wersje i zależności](versions-and-dependencies.md).

Aby uzyskać listę wersji .NET Framework zainstalowanych na komputerze, można uzyskać dostęp do rejestru. Możesz użyć Edytora rejestru, aby wyświetlić rejestr lub użyć kodu, aby wykonać zapytanie:

- Znajdź nowsze wersje .NET Framework (4,5 i nowsze):
  - [Znajdź .NET Framework wersje przy użyciu Edytora rejestru](#net_b)
  - [Używanie kodu do wysyłania zapytań do rejestru w przypadku wersji .NET Framework](#net_d)
  - [Używanie programu PowerShell do wykonywania zapytań dotyczących rejestru w przypadku wersji .NET Framework](#ps_a)
- Znajdź starsze wersje .NET Framework (1&#8211;4):
  - [Znajdź .NET Framework wersje przy użyciu Edytora rejestru](#net_a)
  - [Używanie kodu do wysyłania zapytań do rejestru w przypadku wersji .NET Framework](#net_c)

Aby uzyskać listę wersji środowiska CLR zainstalowanych na komputerze, użyj narzędzia lub kodu:

- [Korzystanie z narzędzia Clrver](#clr_a)
- [Użyj kodu, aby wykonać zapytanie dotyczące klasy środowiska](#clr_b)

Aby uzyskać informacje dotyczące wykrywania zainstalowanych aktualizacji dla każdej wersji .NET Framework, zobacz [How to: Określanie, które aktualizacje .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md).

## <a name="find-newer-net-framework-versions-45-and-later"></a>Znajdź nowsze wersje .NET Framework (4,5 i nowsze)

<a name="net_b"></a>

### <a name="find-net-framework-versions-45-and-later-in-the-registry"></a>Znajdź .NET Framework w wersji 4,5 i nowszych w rejestrze

1. Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.

     Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.

2. W Edytorze rejestru Otwórz następujący podklucz: **rejestrze Framework Setup\NDP\v4\Full**. Jeśli **pełny** podklucz nie jest obecny, nie masz zainstalowanego .NET Framework 4,5 lub nowszego.

    > [!NOTE]
    > Folder **instalacji programu .NET Framework** w rejestrze *nie rozpoczyna się* kropką.

3. Wyszukaj wpis DWORD o nazwie **Release**. Jeśli istnieje, masz zainstalowaną .NET Framework 4,5 lub nowszą wersję. Wartość jest kluczem wydania, który odpowiada określonej wersji .NET Framework. Na przykład, wartość wpisu **zlecenia** to *378389*, który jest kluczem wydania dla .NET Framework 4,5.

     ![Wpis rejestru dla .NET Framework 4,5](./media/clr-installdir.png "Wpis rejestru dla .NET Framework 4,5")

W poniższej tabeli wymieniono wartości DWORD **wydania** w poszczególnych systemach operacyjnych dla .NET Framework 4,5 i nowszych.

[!INCLUDE[Release key values note](~/includes/version-keys-note.md)]

<a name="version_table"></a>

|Wersja programu .NET Framework|Wartość DWORD dotycząca wersji|
|--------------------------------|-------------|
|.NET Framework 4.5|Wszystkie systemy operacyjne Windows: 378389|
|.NET Framework 4.5.1|W systemach Windows 8.1 i Windows Server 2012 R2:378675<br />We wszystkich innych systemach operacyjnych Windows: 378758|
|.NET Framework 4.5.2|Wszystkie systemy operacyjne Windows: 379893|
|.NET Framework 4.6|W systemie Windows 10:393295<br />We wszystkich innych systemach operacyjnych Windows: 393297|
|.NET Framework 4.6.1|W systemach aktualizacji systemu Windows 10 listopad: 394254<br />We wszystkich innych systemach operacyjnych Windows (w tym Windows 10): 394271|
|.NET Framework 4.6.2|W rocznicowej aktualizacji systemu Windows 10 i Windows Server 2016:394802<br />Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 394806|
|.NET Framework 4,7|Aktualizacja systemu Windows 10 dla twórców: 460798<br />Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 460805|
|.NET Framework 4.7.1|W przypadku aktualizacji systemu Windows 10 dla twórców i systemu Windows Server w wersji 1709:461308<br/>Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 461310|
|.NET Framework 4.7.2|W systemie Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461808<br/>We wszystkich systemach operacyjnych Windows innych niż Windows 10 kwiecień 2018 Update i Windows Server w wersji 1803:461814|
|.NET Framework 4,8|W systemie Windows 10 maja 2019 Update i aktualizacja Windows 10 listopad 2019:528040<br/>Wszystkie inne systemy operacyjne Windows (w tym inne systemy operacyjne Windows 10): 528049|

Możesz użyć następujących wartości w następujący sposób:

- Aby określić, czy określona wersja .NET Framework jest zainstalowana w określonej wersji systemu operacyjnego Windows, należy sprawdzić, czy wartość DWORD **wersji** jest *równa* wartości wymienionej w tabeli. Na przykład aby określić, czy .NET Framework 4,6 jest obecny w systemie Windows 10, należy sprawdzić wartość **wersji** , która jest *równa* 393295.

- Aby określić, czy jest dostępna minimalna wersja .NET Framework, Użyj mniejszej wartości DWORD **Release** dla tej wersji. Na przykład, jeśli aplikacja działa w .NET Framework 4,6 lub nowszej wersji, należy przetestować wartość typu DWORD **zlecenia** , która jest *większa lub równa* 393295. W przypadku tabeli, która zawiera tylko minimalną wartość **typu DWORD dla każdej wersji .NET Framework** , zobacz [minimalne wartości w polu dword wydania dla .NET Framework 4,5 i nowszych wersji](minimum-release-dword.md).

- Aby przetestować dla wielu wersji, Zacznij od sprawdzenia wartości, która jest *większa niż lub równa* mniejszej wartości DWORD dla najnowszej wersji .NET Framework, a następnie porównaj wartość z mniejszą wartością DWORD dla każdej kolejnej wersji. Na przykład, jeśli aplikacja wymaga .NET Framework 4,7 lub nowszego, a chcesz określić konkretną wersję .NET Framework obecny, Zacznij od testowania dla wartości typu DWORD o **wersji** , która jest *większa lub równa* 461808 (mniejsza wartość DWORD wartość .NET Framework 4.7.2). Następnie porównaj wartość DWORD **wersji** z mniejszą wartością dla każdej późniejszej .NET Framework wersji. W przypadku tabeli, która zawiera tylko minimalną wartość **typu DWORD dla każdej wersji .NET Framework** , zobacz [minimalne wartości w polu dword wydania dla .NET Framework 4,5 i nowszych wersji](minimum-release-dword.md).

<a name="net_d"></a>

### <a name="find-net-framework-versions-45-and-later-with-code"></a>Znajdź .NET Framework wersje 4,5 i nowsze z kodem

1. Użyj metod <xref:Microsoft.Win32.RegistryKey.OpenBaseKey%2A?displayProperty=nameWithType> i <xref:Microsoft.Win32.RegistryKey.OpenSubKey%2A?displayProperty=nameWithType>, aby uzyskać dostęp do podklucza **rejestrze Framework Setup\NDP\v4\Full** w rejestrze systemu Windows.

    Obecność wpisu DWORD **Release** w podkluczu **rejestrze Framework Setup\NDP\v4\Full** wskazuje, że na komputerze jest zainstalowana .NET Framework 4,5 lub nowsza.

2. Sprawdź wartość wpisu **Zwolnij** , aby określić zainstalowaną wersję. Aby można było przesłać dalej, sprawdź, czy wartość jest większa niż lub równa wartości wymienionej w [tabeli wersji .NET Framework](#version_table).

Poniższy przykład sprawdza wartość wpisu **Release** w rejestrze, aby znaleźć .NET Framework 4,5 i nowsze wersje, które są zainstalowane:

[!code-csharp[ListVersions#5](../../../samples/snippets/csharp/framework/migration-guide/versions-installed3.cs)]
[!code-vb[ListVersions#5](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed3.vb)]

Ten przykład jest zgodny z zalecaną metodą sprawdzania wersji:

- Sprawdza, czy wartość wpisu **wydania** jest *większa niż lub równa* wartości znanych kluczy wydania.

- Sprawdza w kolejności od najnowszej wersji do najwcześniejszej wersji.

<a name="ps_a"></a>

### <a name="check-for-a-minimum-required-net-framework-version-45-and-later-with-powershell"></a>Sprawdzanie minimalnej wymaganej wersji .NET Framework (4,5 i nowszych) przy użyciu programu PowerShell

- Użyj poleceń programu PowerShell, aby sprawdzić wartość wpisu **Release** w podkluczu **rejestrze Framework Setup\NDP\v4\Full** .

Poniższe przykłady umożliwiają sprawdzenie wartości wpisu **wydania** , aby określić, czy .NET Framework 4.6.2 lub nowszy. Ten kod zwraca `True`, jeśli jest zainstalowany i `False` w przeciwnym razie.

```PowerShell
(Get-ItemProperty "HKLM:SOFTWARE\Microsoft\NET Framework Setup\NDP\v4\Full").Release -ge 394802
```

Aby sprawdzić, czy wersja .NET Framework wymaga innej minimalnej wersji, Zastąp *394802* w poniższych przykładach wartością **wydania** z [tabeli .NET Framework wersji](#version_table).

## <a name="find-older-net-framework-versions-182114"></a>Znajdź starsze wersje .NET Framework (1&#8211;4)

<a name="net_a"></a>

### <a name="find-net-framework-versions-182114-in-the-registry"></a>Znajdź .NET Framework wersji 1&#8211;4 w rejestrze

1. Z menu **Start** wybierz polecenie **Uruchom**, wpisz polecenie *regedit*, a następnie wybierz przycisk **OK**.

    Musisz mieć poświadczenia administracyjne, aby uruchomić regedit.

2. W Edytorze rejestru Otwórz następujący podklucz: **rejestrze Framework Setup\NDP**:

    - W przypadku .NET Framework wersje 1,1 do 3,5 każda zainstalowana wersja jest wymieniona jako podklucz w podkluczu **rejestrze Framework Setup\NDP** . Na przykład **rejestrze Framework Setup\NDP\v3.5**. Numer wersji jest przechowywany jako wartość w wpisie **wersji** podklucza wersji.

    - W przypadku .NET Framework 4, wpis **wersji** znajduje się w podkluczu **rejestrze Framework Setup\NDP\v4.0\Client** , **rejestrze Framework Setup\NDP\v4.0\Full** podklucz lub w obu podkluczach.

    > [!NOTE]
    > Folder **instalacji programu .NET Framework** w rejestrze nie rozpoczyna się kropką.

    Na poniższej ilustracji przedstawiono podklucz i jego **wersję** wpisu dla .NET Framework 3,5.

    ![Wpis rejestru dla .NET Framework 3,5.](./media/net-4-and-earlier.png ".NET Framework 3,5 i wcześniejsze wersje")

<a name="net_c"></a>

### <a name="find-net-framework-versions-182114-with-code"></a>Znajdź .NET Framework wersje 1&#8211;4 z kodem

- Użyj klasy <xref:Microsoft.Win32.RegistryKey?displayProperty=nameWithType>, aby uzyskać dostęp do podklucza **rejestrze Framework Setup\NDP** w rejestrze systemu Windows.

Poniższy przykład umożliwia znalezienie zainstalowanych wersji .NET Framework&#8211;1 4:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed1.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed1.vb)]

## <a name="find-clr-versions"></a>Znajdź wersje środowiska CLR

<a name="clr_a"></a>

### <a name="find-the-current-clr-version-with-clrverexe"></a>Znajdź bieżącą wersję środowiska CLR za pomocą Clrver. exe

Użyj [Narzędzia wersji środowiska CLR (Clrver. exe)](../tools/clrver-exe-clr-version-tool.md) , aby określić, które wersje środowiska CLR są zainstalowane na komputerze:

- W [wiersz polecenia dla deweloperów dla programu Visual Studio](../tools/developer-command-prompt-for-vs.md)wprowadź `clrver`.

    Przykładowe dane wyjściowe:

    ```console
    Versions installed on the machine:
    v2.0.50727
    v4.0.30319
    ```

<a name="clr_b"></a>

### <a name="find-the-current-clr-version-with-the-environment-class"></a>Znajdź bieżącą wersję środowiska CLR z klasą środowiska

> [!IMPORTANT]
> W przypadku .NET Framework 4,5 i nowszych wersje nie należy używać właściwości <xref:System.Environment.Version%2A?displayProperty=nameWithType> do wykrywania wersji środowiska CLR. Zamiast tego należy wykonać zapytanie dotyczące rejestru zgodnie z opisem w artykule [znajdowanie .NET Framework wersje 4,5 i nowsze z kodem](#net_d).

1. Zbadaj Właściwość <xref:System.Environment.Version?displayProperty=nameWithType>, aby pobrać obiekt <xref:System.Version>.

    Zwrócony obiekt `System.Version` identyfikuje wersję środowiska uruchomieniowego, które aktualnie wykonuje kod. Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogły zostać zainstalowane na komputerze.

    W przypadku .NET Framework w wersji 4, 4,5, 4.5.1 i 4.5.2 ciąg reprezentujący zwrócony obiekt <xref:System.Version> ma postać 4.0.30319. *XXXXX*, gdzie *XXXXX* jest mniejszy niż 42000. W przypadku .NET Framework 4,6 i nowszych wersje ma postać 4.0.30319.42000.

2. Po utworzeniu obiektu `Version` wykonaj zapytanie w następujący sposób:

   - Aby uzyskać informacje o głównym identyfikatorze wydania (na przykład *4* dla wersji 4,0), użyj właściwości <xref:System.Version.Major%2A?displayProperty=nameWithType>.

   - W przypadku pomocniczego identyfikatora wydania (na przykład *0* w przypadku wersji 4,0) użyj właściwości <xref:System.Version.Minor%2A?displayProperty=nameWithType>.

   - Dla całego ciągu wersji (na przykład *4.0.30319.18010*) użyj metody <xref:System.Version.ToString%2A?displayProperty=nameWithType>. Ta metoda zwraca pojedynczą wartość odzwierciedlającą wersję środowiska uruchomieniowego, które wykonuje kod. Nie zwraca wersji zestawu ani innych wersji środowiska uruchomieniowego, które mogą być zainstalowane na komputerze.

W poniższym przykładzie zastosowano Właściwość <xref:System.Environment.Version%2A?displayProperty=nameWithType> do pobrania informacji o wersji środowiska CLR:

[!code-csharp[ListVersions](../../../samples/snippets/csharp/framework/migration-guide/versions-installed2.cs)]
[!code-vb[ListVersions](../../../samples/snippets/visualbasic/framework/migration-guide/versions-installed2.vb)]

## <a name="see-also"></a>Zobacz także

- [Instrukcje: Określanie, które aktualizacje .NET Framework są zainstalowane](how-to-determine-which-net-framework-updates-are-installed.md)
- [Zainstaluj .NET Framework dla deweloperów](../install/guide-for-developers.md)
- [.NET Framework wersje i zależności](versions-and-dependencies.md)
