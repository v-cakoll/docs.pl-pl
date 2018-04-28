---
title: Kierowanie dla programu .NET Framework 2.0 w systemie Windows 8
description: 'Informacje o przeznaczonych dla starszej wersji programu .NET Framework przy użyciu języka F #.'
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: 7c9bd8087da94a476105729b6f5b050fc66629a2
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="targeting-older-versions-of-net"></a>Przeznaczony dla starszej wersji programu .NET

> [!NOTE]
W tym artykule nie jest aktualny najnowsze Visual Studio.  Zostaną zaktualizowane.

Następujący błąd może wystąpić, Jeśli spróbujesz docelową programu .NET Framework 2.0, 3.0 lub 3.5 w języku F # projektu programu Visual Studio jest zainstalowany na Windows 8.1: 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

Wiadomo, że ten błąd występuje w następujących kombinacji warunki:


- Visual Studio jest zainstalowany na Windows 8.1.
<br />

- Nie można włączyć program .NET Framework 3.5 przed zainstalowaniem programu Visual Studio.
<br />

- Projekt jest przeznaczony dla programu .NET Framework 2.0, 3.0 lub 3.5.
<br />

Po zainstalowaniu programu Visual Studio wykryje zainstalowanych wersji programu .NET Framework i instaluje środowisko uruchomieniowe 2.0 F # tylko w przypadku programu .NET Framework 3.5 jest zainstalowany i włączony.


## <a name="resolving-the-error"></a>Rozwiązywanie błędu
Aby rozwiązać ten problem, można miejsca docelowego nowszej wersji programu .NET Framework lub należy włączyć dla programu .NET Framework 3.5 na Windows 8.1, a następnie zainstalować środowiska uruchomieniowego języka F # 2.0, uruchamiając Instalatora programu Visual Studio z **naprawy** Opcja.


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Aby włączyć dla programu .NET Framework 3.5 na Windows 8.1

1. Na **Start** ekranu, uruchom, aby wprowadzić **Panelu sterowania**.
<br />  Po wprowadzeniu tej samej nazwie, **Panelu sterowania** ikona jest wyświetlana w obszarze **aplikacji** nagłówka.
<br />

2. Wybierz **Panelu sterowania** ikony, wybierz **programy** ikony, a następnie wybierz pozycję **Włącz lub wyłącz funkcje systemu Windows** łącza.
<br />

3. Upewnij się, że **.NET Framework 3.5 (w tym .NET 2.0 i 3.0)** pole wyboru jest zaznaczone, a następnie wybierz pozycję **OK** przycisku.
<br />  Nie trzeba zaznacz pola wyboru dla dowolnej węzłów podrzędnych dla składników opcjonalnych programu .NET Framework.
<br />  .NET Framework 3.5 jest włączona, jeśli nie był już.
<br />


#### <a name="to-install-the-f-20-runtime"></a>Aby zainstalować środowisko uruchomieniowe języka F # 2.0

1. W Panelu sterowania, wybierz **programy** łącza, a następnie wybierz pozycję **programy i funkcje** łącza.
<br />

2. Na liście zainstalowanych programów, wybierz wersji programu Visual Studio, która jest zainstalowana, a następnie wybierz pozycję **zmiany** przycisku.
<br />

3. Po uruchomieniu Instalatora, wybierz **naprawy** przycisku.
<br />  Aby uzyskać więcej informacji, zobacz [Instalowanie programu Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).
<br />
## <a name="see-also"></a>Zobacz też
[Visual F#](../index.md)
