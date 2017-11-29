---
title: "Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc30145
- bc30145
helpviewer_keywords: BC30145
ms.assetid: 2e7eb2b9-eda6-4bdb-95cc-72c7f0be7528
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 9dcf3d4bec379faa5783ca17847b91f9739df598
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unable-to-emit-assembly-lterror-messagegt"></a>Nie można wyemitować zestawu: &lt;komunikat o błędzie&gt;
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora wywołania Assembly Linker (Al.exe, znanej także jako Alink) można wygenerować zestawu z manifestu, z konsolidatora raportowania błędów w fazie emisji tworzenia zestawu.  
  
 **Identyfikator błędu:** BC30145  
  
## <a name="to-correct-this-error"></a>Aby poprawić ten błąd  
  
1.  Sprawdź ujętego w cudzysłów komunikat i zapoznaj się temacie [Al.exe narzędzia błędy i ostrzeżenia](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b) uzyskać dokładniejsze objaśnienie i porady.  
  
2.  Spróbuj ręcznie, podpisywania zestawu za pomocą [Al.exe (konsolidator zestawów)](https://msdn.microsoft.com/library/c405shex) lub [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23).  
  
3.  Jeśli błąd będzie się powtarzać, zebrać informacje dotyczące okoliczności i powiadomić pomocy technicznej firmy Microsoft.  
  
### <a name="to-sign-the-assembly-manually"></a>Aby ręcznie zarejestrować zestawu  
  
1.  Użyj [Sn.exe (narzędzie silnej nazwy)](https://msdn.microsoft.com/library/k5b5tt23) można utworzyć pliku pary kluczy publiczny/prywatny.  
  
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
  
6.  W [!INCLUDE[vsprvs](~/includes/vsprvs-md.md)], Dodaj odwołanie do zestawu .NET do nowo utworzonego pliku.  
  
## <a name="see-also"></a>Zobacz też  
 [Al.exe (konsolidator zestawów)](https://msdn.microsoft.com/library/c405shex)  
 [Narzędzie Al.exe błędy i ostrzeżenia](http://msdn.microsoft.com/en-us/7f125d49-0a03-47a6-9ba9-d61a679a7d4b)  
 [SN.exe (narzędzie silnych nazw)](https://msdn.microsoft.com/library/k5b5tt23)  
 [Porady: tworzenie pary kluczy publiczno prywatnych](http://msdn.microsoft.com/library/05026813-f3bd-4d7c-9e0b-fc588eb3d114)  
 [Porozmawiaj z nami](/visualstudio/ide/talk-to-us)
