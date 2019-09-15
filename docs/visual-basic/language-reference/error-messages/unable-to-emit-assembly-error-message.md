---
title: 'Nie można wyemitować zestawu: <error message>'
ms.date: 08/14/2018
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 530aaee40be92bf72ee4b83b4141108e9b81c8a1
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70968850"
---
# <a name="unable-to-emit-assembly-error-message"></a>Nie można wyemitować zestawu \<: komunikat o błędzie >

Kompilator Visual Basic wywołuje konsolidator zestawu (*Al. exe*, znany również jako ALink) w celu wygenerowania zestawu z manifestem, a konsolidator raportuje błąd w fazie emisji tworzenia zestawu.

**Identyfikator błędu:** BC30145

## <a name="to-correct-this-error"></a>Aby poprawić ten błąd

1. Sprawdź cytowany komunikat o błędzie i zapoznaj się z tematem [Al. exe](../../../framework/tools/al-exe-assembly-linker.md) , aby uzyskać dokładniejsze wyjaśnienie i porady.

2. Spróbuj podpisać zestaw ręcznie przy użyciu [Al. exe](../../../framework/tools/al-exe-assembly-linker.md) lub [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md).

3. Jeśli błąd będzie się powtarzać, należy zebrać informacje dotyczące okoliczności i powiadom pomoc techniczna firmy Microsoft.

### <a name="to-sign-the-assembly-manually"></a>Aby ręcznie podpisać zestaw

1. Użyj [SN. exe (Narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md), aby utworzyć plik pary kluczy publicznych/prywatnych.

   Ten plik ma rozszerzenie *. snk* .

2. Usuń odwołanie COM, które generuje błąd z projektu.

3. Otwórz [wiersz polecenia dla deweloperów dla programu Visual Studio](../../../framework/tools/developer-command-prompt-for-vs.md).

   W systemie Windows 10 wprowadź **wiersz polecenia programisty** w polu wyszukiwania na pasku zadań. Następnie wybierz pozycję **wiersz polecenia dla deweloperów dla programu VS 2017** z listy wyników.

4. Zmień katalog na katalog, w którym chcesz umieścić otokę zestawu.

5. Wprowadź następujące polecenie:

    ```cmd
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>
    ```

   Przykładem rzeczywistego polecenia, które można wprowadzić:

    ```cmd
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"
    ```

   > [!TIP]
   > Jeśli ścieżka lub plik zawiera spacje, należy użyć podwójnych cudzysłowów.

6. W programie Visual Studio Dodaj odwołanie do zestawu .NET do pliku, który właśnie został utworzony.

## <a name="see-also"></a>Zobacz także

- [Al.exe](../../../framework/tools/al-exe-assembly-linker.md)
- [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md)
- [Instrukcje: Tworzenie pary kluczy publiczny-prywatny](../../../standard/assembly/create-public-private-key-pair.md)
- [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
