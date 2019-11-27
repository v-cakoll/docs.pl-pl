---
title: /debug
ms.date: 03/10/2018
helpviewer_keywords:
- debug compiler switches
- /debug compiler option [Visual Basic]
- -debug compiler option [Visual Basic]
- debug compiler option [Visual Basic]
ms.assetid: c2b0bea5-1d5e-499f-9bd5-4f6c6b715ea2
ms.openlocfilehash: 3beb9ad3829c2f55120a9136e6e54185551bd20b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344782"
---
# <a name="-debug-visual-basic"></a>-Debug (Visual Basic)

Powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w plikach wyjściowych.

## <a name="syntax"></a>Składnia

```console
-debug[+ | -]
```

lub

```console
-debug:[full | pdbonly]
```

## <a name="arguments"></a>Argumenty

|Termin|Definicja|
|---|---|
|`+` &#124; `-`|Opcjonalna. Określenie `+` lub `/debug` powoduje, że kompilator generuje informacje o debugowaniu i umieszcza je w pliku. pdb. Określenie `-` ma ten sam skutek, co nie określa `/debug`.|
|`full` &#124; `pdbonly`|Opcjonalna. Określa typ informacji o debugowaniu generowanych przez kompilator. Jeśli nie określisz `/debug:pdbonly`, wartość domyślna to `full`, co umożliwia dołączenie debugera do uruchomionego programu. Argument `pdbonly` umożliwia debugowanie kodu źródłowego, gdy program jest uruchamiany w debugerze, ale wyświetla kod języka asemblera tylko wtedy, gdy uruchomiony program jest dołączony do debugera.|

## <a name="remarks"></a>Uwagi

Użyj tej opcji, aby utworzyć kompilacje debugowania. Jeśli nie określisz `/debug`, `/debug+`lub `/debug:full`, nie będzie można debugować pliku wyjściowego programu.

Domyślnie informacje debugowania nie są emitowane (`/debug-`). Aby emitować informacje o debugowaniu, określ `/debug` lub `/debug+`.

Informacje o sposobie konfigurowania wydajności debugowania aplikacji znajdują się w temacie [ułatwianie debugowania obrazu](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).

|Aby ustawić debugowanie w zintegrowanym środowisku programistycznym programu Visual Studio|
|---|
|1. w projekcie wybranym w **Eksplorator rozwiązań**w menu **projekt** kliknij polecenie **Właściwości**. <br />2. Kliknij kartę **kompilacja** .<br />3. kliknij pozycję **Zaawansowane opcje kompilacji**.<br />4. Zmodyfikuj wartość w polu **Generuj informacje o debugowaniu** .|

## <a name="example"></a>Przykład

Poniższy przykład umieszcza informacje debugowania w pliku wyjściowym `App.exe`.

```console
vbc -debug -out:app.exe test.vb
```

## <a name="see-also"></a>Zobacz także

- [Kompilator wiersza polecenia Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-bugreport](../../../visual-basic/reference/command-line-compiler/bugreport.md)
- [Przykłady kompilacji — wiersze poleceń](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
