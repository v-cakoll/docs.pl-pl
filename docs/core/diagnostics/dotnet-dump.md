---
title: dotnet-dump - .NET Core
description: Instalowanie i używanie narzędzia wiersza polecenia dotnet-dump.
ms.date: 10/14/2019
ms.openlocfilehash: 3c0e28d4efc96ae53ec7dfae243725ab400e6b8f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "76737674"
---
# <a name="dump-collection-and-analysis-utility-dotnet-dump"></a>Narzędzie do zbierania`dotnet-dump`i analizy zrzutów ( )

**Ten artykuł dotyczy:** ✔️ .NET Core 3.0 SDK i nowszych wersji

> [!NOTE]
> `dotnet-dump`nie jest obsługiwana w systemie macOS.

## <a name="installing-dotnet-dump"></a>Instalowanie`dotnet-dump`

Aby zainstalować najnowszą `dotnet-dump` wersję [pakietu NuGet,](https://www.nuget.org/packages/dotnet-dump)użyj polecenia [instalacji narzędzia dotnet:](../tools/dotnet-tool-install.md)

```dotnetcli
dotnet tool install -g dotnet-dump
```

## <a name="synopsis"></a>Streszczenie

```console
dotnet-dump [-h|--help] [--version] <command>
```

## <a name="description"></a>Opis

Globalne `dotnet-dump` narzędzie jest sposobem zbierania i analizowania zrzutów systemu Windows i `lldb` Linux bez natywnego debugera, takiego jak linux. To narzędzie jest ważne na platformach `lldb` takich jak Alpine Linux, gdzie w pełni działa nie jest dostępna. Narzędzie `dotnet-dump` umożliwia uruchamianie poleceń SOS do analizowania awarii i modułu odśmiecania pamięci (GC), ale nie jest natywnym debugerem, więc takie rzeczy jak wyświetlanie natywnych ramek stosu nie są obsługiwane.

## <a name="options"></a>Opcje

- **`--version`**

  Wyświetla wersję narzędzia dotnet-counters.

- **`-h|--help`**

  Pokazuje pomoc wiersza polecenia.

## <a name="commands"></a>Polecenia

| Polecenie                                     |
| ------------------------------------------- |
| [zbieranie dotnet-dump](#dotnet-dump-collect) |
| [analiza dotnet-dump](#dotnet-dump-analyze) |

## <a name="dotnet-dump-collect"></a>zbieranie dotnet-dump

Przechwytuje zrzut z procesu.

### <a name="synopsis"></a>Streszczenie

```console
dotnet-dump collect [-h|--help] [-p|--process-id] [--type] [-o|--output] [--diag]
```

### <a name="options"></a>Opcje

- **`-h|--help`**

  Pokazuje pomoc wiersza polecenia.

- **`-p|--process-id <PID>`**

  Określa numer identyfikatora procesu, z który ma zostać zrealizowane zrzut pamięci.

- **`--type <Heap|Mini>`**

  Określa typ zrzutu, który określa rodzaje informacji, które są zbierane z procesu. Istnieją dwa typy:

  - `Heap`- Duży i stosunkowo wszechstronny zrzut zawierający listy modułów, listy wątków, wszystkie stosy, informacje o wyjątkach, informacje o obsłudze i całą pamięć z wyjątkiem mapowanych obrazów.
  - `Mini`- Mały zrzut zawierający listy modułów, listy wątków, informacje o wyjątkach i wszystkie stosy.

  Jeśli nie zostanie `Heap` określony, jest ustawieniem domyślnym.

- **`-o|--output <output_dump_path>`**

  Pełna ścieżka i nazwa pliku, w których należy zapisać zebrane zrzuty.

  Jeśli nie określono:

  - Domyślnie *.\dump_YYYYMMDD_HHMMSS.dmp* w systemie Windows.
  - Domyślnie *./core_YYYYMMDD_HHMMSS* w systemie Linux.

  YYYYMMDD jest rok / miesiąc / dzień i HHMMSS jest godzina / minuta / sekunda.

- **`--diag`**

  Włącza rejestrowanie diagnostyczne zbierania zrzutu.

## <a name="dotnet-dump-analyze"></a>analiza dotnet-dump

Uruchamia powłokę interaktywną w celu zbadania zrzutu. Powłoka akceptuje różne [polecenia SOS](#analyze-sos-commands).

### <a name="synopsis"></a>Streszczenie

```console
dotnet-dump analyze <dump_path> [-h|--help] [-c|--command]
```

### <a name="arguments"></a>Argumenty

- **`<dump_path>`**

  Określa ścieżkę do pliku zrzutu do analizy.

### <a name="options"></a>Opcje

- **`-c|--command <debug_command>`**

  Określa [polecenie](#analyze-sos-commands) do uruchomienia w powłoce przy starcie.

### <a name="analyze-sos-commands"></a>Analizowanie poleceń SOS

| Polecenie                             | Funkcja                                                                                      |
| ----------------------------------- | --------------------------------------------------------------------------------------------- |
| `soshelp`                           | Wyświetla wszystkie dostępne polecenia                                                               |
| `soshelp|help <command>`            | Wyświetla określone polecenie.                                                               |
| `exit|quit`                         | Kończy tryb interakcyjny.                                                                       |
| `clrstack <arguments>`              | Dostarcza ślad stosu wyłącznie dla kodu zarządzanego.                                                  |
| `clrthreads <arguments>`            | Wyświetla listę uruchomionych wątków zarządzanych.                                                            |
| `dumpasync <arguments>`             | Wyświetla informacje o maszynach stanu asynchronicznego na stercie zebranych w pamięci.                |
| `dumpassembly <arguments>`          | Wyświetla szczegóły dotyczące złożenia.                                                           |
| `dumpclass <arguments>`             | Wyświetla informacje o strukturze klasy EE pod określonym adresem.                     |
| `dumpdelegate <arguments>`          | Wyświetla informacje o pełnomocniku.                                                        |
| `dumpdomain <arguments>`            | Wyświetla informacje o wszystkich domenach aplikacji i wszystkich zestawach w domenach.                |
| `dumpheap <arguments>`              | Wyświetla informacje o stercie zebrane jułtów i statystyki kolekcji dotyczące obiektów.       |
| `dumpil <arguments>`                | Wyświetla język pośredni Microsoft (MSIL) skojarzony z zarządzaną metodą. |
| `dumplog <arguments>`               | Zapisuje zawartość dziennika obciążenia pamięci do określonego pliku.                         |
| `dumpmd <arguments>`                | Wyświetla informacje o methoddesc struktury na określony adres.                   |
| `dumpmodule <arguments>`            | Wyświetla informacje o strukturze modułu EE pod określonym adresem.                    |
| `dumpmt <arguments>`                | Wyświetla informacje dotyczące tabeli metod pod podanym adresem.                           |
| `dumpobj <arguments>`               | Wyświetla informacje o obiekcie pod określonym adresem.                                       |
| `dso|dumpstackobjects <arguments>`  | Wyświetla wszystkie zarządzane obiekty znalezione w granicach bieżącego stosu.                    |
| `eeheap <arguments>`                | Wyświetla informacje o pamięci procesowej używanej przez wewnętrzne struktury danych w czasie wykonywania.              |
| `finalizequeue <arguments>`         | Wyświetla wszystkie obiekty zarejestrowane dla finalizacji.                                             |
| `gcroot <arguments>`                | Wyświetla informacje o odwołaniach (lub katalogach głównych) do obiektu pod określonym adresem.              |
| `gcwhere <arguments>`               | Wyświetla lokalizację w stercie GC przekazanego argumentu.                               |
| `ip2md <arguments>`                 | Wyświetla MethodDesc struktury pod określonym adresem w kodzie JIT.                       |
| `histclear <arguments>`             | Zwalnia wszystkie zasoby używane `hist*` przez rodzinę poleceń.                                |
| `histinit <arguments>`              | Inicjuje struktury SOS z dziennika obciążenia zapisanego w obiekcie debugowanym.                     |
| `histobj <arguments>`               | Wyświetla przenoszenie dziennika podprężeń wyrzucania `<arguments>`elementów bezużytecznych związane z .              |
| `histobjfind <arguments>`           | Wyświetla wszystkie wpisy dziennika, które odwołują się do obiektu pod podanym adresem.               |
| `histroot <arguments>`              | Wyświetla informacje powiązane zarówno z promocjami, jak i przeniesieniami określonego korzenia.        |
| `lm|modules`                        | Wyświetla moduły macierzyste w procesie.                                                   |
| `name2ee <arguments>`               | Wyświetla strukturę MethodTable i EEClass `<argument>`dla pliku .                |
| `pe|printexception <arguments>`     | Wyświetla dowolny obiekt pochodzący z Exception `<argument>`klasy na adres .             |
| `setsymbolserver <arguments>`       | Włącza obsługę serwera symboli                                                             |
| `syncblk <arguments>`               | Wyświetla informacje o posiadaczu SyncBlock.                                                           |
| `threads|setthread <threadid>`      | Ustawia lub wyświetla bieżący identyfikator wątku dla poleceń SOS.                                  |

## <a name="using-dotnet-dump"></a>Używanie elementu `dotnet-dump`

Pierwszym krokiem jest zebranie zrzutu. Ten krok można pominąć, jeśli zrzut rdzenia został już wygenerowany. System operacyjny lub funkcja generowania zrzutów w czasie wykonywania .NET Core [może](https://github.com/dotnet/runtime/blob/master/docs/design/coreclr/botr/xplat-minidump-generation.md) tworzyć zrzuty rdzenia.

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

Ta akcja powoduje wyświetlenie interaktywnej sesji, która akceptuje polecenia, takie jak:

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

Aby zobaczyć nieobsługiwany wyjątek, który zabił aplikację:

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

Jeśli używasz w obszarze Docker, `SYS_PTRACE` zbieranie zrzutu wymaga możliwości (`--cap-add=SYS_PTRACE` lub `--privileged`).

W przypadku obrazów platformy Docker systemu `dotnet-dump` Microsoft .NET Core SDK Linux niektóre polecenia mogą zgłaszać następujący wyjątek:

> Nieobsługiwany wyjątek: System.DllNotFoundException: Nie można załadować biblioteki udostępnionej "libdl.so" lub jednego z jego zależności wyjątek.

Aby obejść ten problem, zainstaluj pakiet "libc6-dev".
