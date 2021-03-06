---
title: zrzut dotnet - .NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: c78ddb6447021f61f2452c075733b7d33e051ca0
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888205"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Narzędzie do zbierania`dotnet-dump`i analizy zrzutu ( )

**Ten artykuł dotyczy:** ✔️.NET Core 3.0 SDK i nowszych wersjach

> [!NOTE]
> `dotnet-dump`nie jest obsługiwana w systemie macOS.

## <a name="installing-dotnet-dump"></a>Instalowanie`dotnet-dump`

Aby zainstalować najnowszą wersję `dotnet-dump` [pakietu NuGet,](https://www.nuget.org/packages/dotnet-dump)użyj polecenia [instalowania narzędzia dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Streszczenie

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Opis

Globalne `dotnet-dump` narzędzie jest sposobem na zbieranie i analizowanie zrzutów systemu Windows `lldb` i Linux bez udziału natywnego debugera, takiego jak linux. To narzędzie jest ważne na platformach `lldb` takich jak Alpine Linux, gdzie w pełni działające nie jest dostępne. Narzędzie `dotnet-dump` umożliwia uruchamianie poleceń SOS do analizowania awarii i modułu zbierającego elementy bezużyteczne (GC), ale nie jest natywnym debugerem, więc takie rzeczy jak wyświetlanie ramek stosu macierzystego nie są obsługiwane.

## <a name="options"></a>Opcje

- **`--version`**

  Wyświetla wersję narzędzia dotnet-dump.

- **`-h|--help`**

  Pokazuje pomoc wiersza polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                     |
| ------------------------------------------- |
| [zbierać zrzut dotnet](#dotnet-dump-collect) |
| [analiza zrzutu dotnet](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>zbierać zrzut dotnet

Przechwytuje zrzut z procesu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Opcje

- **`-h|--help`**

  Pokazuje pomoc wiersza polecenia.

- **`-p|--process-id <PID>`**

  Określa numer identyfikatora procesu, z wyliczyć zrzut pamięci.

- **`--type <Heap|Mini>`**

  Określa typ zrzutu, który określa rodzaje informacji, które są zbierane z procesu. Istnieją dwa typy:

  - `Heap`- Duży i stosunkowo kompleksowy zrzut zawierający listy modułów, listy wątków, wszystkie stosy, informacje o wyjątkach, informacje o obsłudze i całą pamięć z wyjątkiem mapowanych obrazów.
  - `Mini`- Mały zrzut zawierający listy modułów, listy wątków, informacje o wyjątkach i wszystkie stosy.

  Jeśli nie `Heap` zostanie określony, jest wartością domyślną.

- **`-o|--output <output_dump_path>`**

  Pełna ścieżka i nazwa pliku, w którym należy zapisać zebrany zrzut.

  Jeśli nie określono:

  - Wartość domyślna to *.\dump_YYYYMMDD_HHMMSS.dmp* w systemie Windows.
  - Domyślnie *wartość ./core_YYYYMMDD_HHMMSS* w systemie Linux.

  RRRRMMDD to rok/miesiąc/dzień, a HHMMSS to godzina/minuta/sekunda.

- **`--diag`**

  Umożliwia rejestrowanie diagnostyczne zbierania zrzutów.

## <a name="dotnet-dump-analyze"></a>analiza zrzutu dotnet

Uruchamia powłokę interaktywną, aby eksplorować zrzut. Powłoka akceptuje różne [polecenia SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Streszczenie

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Argumenty

- **`<dump_path>`**

  Określa ścieżkę do pliku zrzutu do analizy.

### <a name="options"></a>Opcje

- **`-c|--command <debug_command>`**

  Określa [polecenie](#analyze-sos-commands) do uruchomienia w powłoce na początku.

### <a name="analyze-sos-commands"></a>Analizowanie poleceń SOS

| Polecenie                             | Funkcja                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Wyświetla wszystkie dostępne polecenia                                                               |
| `soshelp|help <command>`            | Wyświetla określone polecenie.                                                               |
| `exit|quit`                         | Wychodzi z trybu interaktywnego.                                                                       |
| `clrstack <arguments>`              | Dostarcza ślad stosu wyłącznie dla kodu zarządzanego.                                                  |
| `clrthreads <arguments>`            | Wyświetla listę uruchomionych wątków zarządzanych.                                                            |
| `dumpasync <arguments>`             | Wyświetla informacje o maszynach stanu asynchronii na stercie zebranej śmieci.                |
| `dumpassembly <arguments>`          | Wyświetla szczegóły dotyczące złożenia.                                                           |
| `dumpclass <arguments>`             | Wyświetla informacje o strukturze klasy EE pod określonym adresem.                     |
| `dumpdelegate <arguments>`          | Wyświetla informacje o pełnomocniku.                                                        |
| `dumpdomain <arguments>`            | Wyświetla informacje wszystkie AppDomains i wszystkie zestawy w domenach.                |
| `dumpheap <arguments>`              | Wyświetla informacje o sterty zebranej przez odpady i statystyki kolekcji obiektów.       |
| `dumpil <arguments>`                | Wyświetla język pośredni Microsoft (MSIL) skojarzony z zarządzaną metodą. |
| `dumplog <arguments>`               | Zapisuje zawartość dziennika obciążenia pamięci do określonego pliku.                         |
| `dumpmd <arguments>`                | Wyświetla informacje o strukturze MetodyDesc pod określonym adresem.                   |
| `dumpmodule <arguments>`            | Wyświetla informacje o strukturze modułu EE pod określonym adresem.                    |
| `dumpmt <arguments>`                | Wyświetla informacje dotyczące tabeli metod pod podanym adresem.                           |
| `dumpobj <arguments>`               | Wyświetla informacje o obiekcie pod określonym adresem.                                       |
| `dso|dumpstackobjects <arguments>`  | Wyświetla wszystkie zarządzane obiekty znalezione w granicach bieżącego stosu.                    |
| `eeheap <arguments>`                | Wyświetla informacje o pamięci procesowej zużywanej przez wewnętrzne struktury danych środowiska wykonawczego.              |
| `finalizequeue <arguments>`         | Wyświetla wszystkie obiekty zarejestrowane dla finalizacji.                                             |
| `gcroot <arguments>`                | Wyświetla informacje o odwołaniach (lub korzeniach) do obiektu pod określonym adresem.              |
| `gcwhere <arguments>`               | Wyświetla lokalizację w stercie GC argumentu przekazanego.                               |
| `ip2md <arguments>`                 | Wyświetla strukturę MethodDesc pod określonym adresem w kodzie JIT.                       |
| `histclear <arguments>`             | Zwalnia wszystkie zasoby używane `hist*` przez rodzinę poleceń.                                |
| `histinit <arguments>`              | Inicjuje struktury SOS z dziennika obciążenia zapisanego w obiekcie debugowanym.                     |
| `histobj <arguments>`               | Wyświetla relokacje dziennika naprężeń wyrzucania elementów bezużytecznych związane z programem `<arguments>`.              |
| `histobjfind <arguments>`           | Wyświetla wszystkie wpisy dziennika, które odwołują się do obiektu pod podanym adresem.               |
| `histroot <arguments>`              | Wyświetla informacje powiązane zarówno z promocjami, jak i przeniesieniami określonego korzenia.        |
| `lm|modules`                        | Wyświetla moduły macierzyste w procesie.                                                   |
| `name2ee <arguments>`               | Wyświetla strukturę MethodTable i EEClass dla . `<argument>`                |
| `pe|printexception <arguments>`     | Wyświetla dowolny obiekt pochodzący z exception `<argument>`klasy pod adresem .             |
| `setsymbolserver <arguments>`       | Włącza obsługę serwera symboli                                                             |
| `syncblk <arguments>`               | Wyświetla informacje o posiadaczu SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Ustawia lub wyświetla bieżący identyfikator wątku dla poleceń SOS.                                  |

## <a name="using-dotnet-dump"></a>Używanie elementu `dotnet-dump`

Pierwszym krokiem jest zebranie zrzutu. Ten krok można pominąć, jeśli zrzut podstawowy został już wygenerowany. Wbudowany system operacyjny lub [funkcja generowania zrzutu](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) .NET Core może tworzyć zrzuty rdzenia.

```console
$ dotnet-dump collect --process-id 1902
Writing minidump to file ./core_20190226_135837
Written 98983936 bytes (24166 pages) to core file
Complete
```

Teraz przeanalizuj `analyze` zrzut rdzenia za pomocą polecenia:

```console
$ dotnet-dump analyze ./core_20190226_135850
Loading core dump: ./core_20190226_135850
Ready to process analysis commands. Type 'help' to list available commands or 'help [command]' to get detailed help on a command.
Type 'quit' or 'exit' to exit the session.
>
```

Ta akcja wywołuje interaktywną sesję, która akceptuje polecenia, takie jak:

```console
> clrstack
OS Thread Id: 0x573d (0)
    Child SP               IP Call Site
00007FFD28B42C58 00007fb22c1a8ed9 [HelperMethodFrame_PROTECTOBJ: 00007ffd28b42c58] System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo) [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.Program.Foo4(System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.Program.Foo2(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.Program.Foo1(Int32, System.String) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.Program.Main(System.String[]) [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]
00007FFD28B43210 00007fb22aa9cedf [GCFrame: 00007ffd28b43210]
00007FFD28B43610 00007fb22aa9cedf [GCFrame: 00007ffd28b43610]
```

Aby wyświetlić nieobsługiowany wyjątek, który zabił Twoją aplikację:

```console
> pe -lines
Exception object: 00007fb18c038590
Exception type:   System.Reflection.TargetInvocationException
Message:          Exception has been thrown by the target of an invocation.
InnerException:   System.Exception, Use !PrintException 00007FB18C038368 to see more.
StackTrace (generated):
SP               IP               Function
00007FFD28B42DD0 0000000000000000 System.Private.CoreLib.dll!System.RuntimeMethodHandle.InvokeMethod(System.Object, System.Object[], System.Signature, Boolean, Boolean)
00007FFD28B42DD0 00007FB1B1334F67 System.Private.CoreLib.dll!System.Reflection.RuntimeMethodInfo.Invoke(System.Object, System.Reflection.BindingFlags, System.Reflection.Binder, System.Object[], System.Globalization.CultureInfo)+0xa7 [/root/coreclr/src/mscorlib/src/System/Reflection/RuntimeMethodInfo.cs @ 472]
00007FFD28B42E20 00007FB1B18D33ED SymbolTestApp.dll!SymbolTestApp.Program.Foo4(System.String)+0x15d [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 54]
00007FFD28B42ED0 00007FB1B18D2FC4 SymbolTestApp.dll!SymbolTestApp.Program.Foo2(Int32, System.String)+0x34 [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 29]
00007FFD28B42F00 00007FB1B18D2F5A SymbolTestApp.dll!SymbolTestApp.Program.Foo1(Int32, System.String)+0x3a [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 24]
00007FFD28B42F30 00007FB1B18D168E SymbolTestApp.dll!SymbolTestApp.Program.Main(System.String[])+0x6e [/home/mikem/builds/SymbolTestApp/SymbolTestApp/SymbolTestApp.cs @ 19]

StackTraceString: <none>
HResult: 80131604
```

## <a name="special-instructions-for-docker"></a>Specjalne instrukcje dotyczące platformy Docker

Jeśli korzystasz z platformy Docker, `SYS_PTRACE` zbieranie zrzutów wymaga możliwości (`--cap-add=SYS_PTRACE` lub `--privileged`).

W przypadku obrazów platformy Docker programu Microsoft `dotnet-dump` .NET Core SDK Linux niektóre polecenia mogą zgłaszać następujący wyjątek:

> Nieobsługiwał wyjątek: System.DllNotFoundException: Nie można załadować biblioteki udostępnionej "libdl.so" lub jeden z jego zależności wyjątek.

Aby obejść ten problem, zainstaluj pakiet "libc6-dev".
