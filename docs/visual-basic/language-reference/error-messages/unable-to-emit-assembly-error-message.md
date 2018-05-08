---
title: 'Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;'
ms.date: 07/20/2015
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords:
- BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
ms.openlocfilehash: 8f497069088ad30a3be58d02caa0a32f7f1b21b7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;
Kompilator Visual Basic wywołania Assembly Linker (Al.exe, znanej także jako Alink) można wygenerować zestawu z manifestu, z konsolidatora raportowania błędów w fazie emisji tworzenia zestawu.  
  
 **Identyfikator błędu:** BC30145  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe](../../../framework/tools/al-exe-assembly-linker.md). Aby uzyskać dokładniejsze objaśnienie i porady.  
  
2.  Spróbuj ręcznie, podpisywania zestawu za pomocą [Al.exe](../../../framework/tools/al-exe-assembly-linker.md) lub [Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md).  
  
3.  Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.  
  
### <a name="to-sign-the-assembly-manually"></a>Aby ręcznie zarejestrować zestawu  
  
1.  Użyj [Sn.exe (narzędzie silnej nazwy)][Sn.exe (narzędzie silnej nazwy)](../../../framework/tools/sn-exe-strong-name-tool.md)) do utworzenia pliku pary kluczy publiczny/prywatny.  
  
     Ten plik ma rozszerzenie .snk —.  
  
2.  Usuń odwołania COM, który generuje błąd z projektu.  
  
3.  Z systemu Windows **Start** menu wskaż **programy**, wskaż polecenie **Microsoft Visual Studio 2008**, wskaż polecenie **programu Visual Studio Tools**, i następnie kliknij przycisk **programu Visual Studio 2008 polecenie wiersza**.  
  
4.  Przenieś do katalogu, w której chcesz umieścić Twojej otoki zestawu.  
  
5.  Wpisz następujący kod.  
  
    ```  
    tlbimp <path to COM reference file> /out:<output assembly name> /keyfile:<path to .snk file>  
    ```  
  
     Przykładem kodu, który może wprowadzić może być poniżej.  
  
    ```  
    tlbimp c:\windows\system32\msi.dll /out:Interop.WindowsInstaller.dll /keyfile:"c:\documents and settings\mykey.snk"  
    ```  
  
     Jeśli ścieżka lub plik zawiera spacje, użyj podwójny cudzysłów (").  
  
6.  W programie Visual Studio Dodaj odwołanie do pliku, który właśnie utworzony zestaw .NET.  
  
## <a name="see-also"></a>Zobacz też  
 
 [Al.exe](../../../framework/tools/al-exe-assembly-linker.md).  
 [Sn.exe (narzędzie silnych nazw)] [Sn.exe (narzędzie silnych nazw)](../../../framework/tools/sn-exe-strong-name-tool.md))  
 [Instrukcje: tworzenie pary kluczy publiczny-prywatny](../../../framework/app-domains/how-to-create-a-public-private-key-pair.md)  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
