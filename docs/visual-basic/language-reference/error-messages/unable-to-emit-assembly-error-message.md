---
title: 'Nie można wyemitować zestawu: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: d564f4f4462a691504297d65575956c5f06691ca
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61936282"
---
# <a name="unable-to-emit-assembly-error-message"></a>Nie można wyemitować zestawu: \<komunikat o błędzie >

Kompilator języka Visual Basic wywołuje Assembly Linker (*Al.exe*, znanego również jako Alink) do generowania zestawów z manifestu i konsolidator zgłasza błąd, na etapie emisji tworzenia zestawu.

**Identyfikator błędu:** BC30145

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź komunikat o błędzie w cudzysłowach i zapoznaj się z tematem [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) uzyskać dokładniejsze objaśnienie i porady.

2. Spróbuj ręcznie, podpisywania zestawu za pomocą [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) lub [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Jeśli błąd będzie się powtarzać, należy zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.

### <a name="to-sign-the-assembly-manually"></a>Aby podpisać zestaw ręcznie

1. Użyj [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md)) można utworzyć pliku pary kluczy publiczny/prywatny.

   Ten plik zawiera *.snk* rozszerzenia.

2. Usuń odwołanie COM, który generuje błąd z projektu.

3. Otwórz [wiersz polecenia programisty dla programu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   W systemie Windows 10, wprowadź **wiersz polecenia dla deweloperów** w polu wyszukiwania na pasku zadań. Następnie wybierz **wiersz polecenia programisty dla programu VS 2017** z listy wyników.

4. Zmień katalog na katalog, w którym chcesz umieścić swoje otoki zestawu.

5. Wprowadź następujące polecenie:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Jest przykładem rzeczywiste polecenia, które możesz wprowadzić:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Jeśli pliku lub ścieżki zawiera spacje, należy użyć podwójnego cudzysłowu.

6. W programie Visual Studio należy dodać odwołanie do zestawu .NET do pliku, który został utworzony.

## <a name="see-also"></a>Zobacz także

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Instrukcje: Tworzenie pary kluczy publiczny prywatny](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)