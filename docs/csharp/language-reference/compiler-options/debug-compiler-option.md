---
title: -debug (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
caps.latest.revision: "19"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 4705fc6fc3e3fa41f46b8617aa23ab507afa0cd1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="debug-c-compiler-options"></a>/debug (opcje kompilatora C#)
**/Debug** opcji powoduje, że kompilator generuje informacje o debugowaniu i umieścić go w pliku danych wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/debug[+ | -]  
/debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Określanie `+`, lub po prostu **/debug**, powoduje, że kompilator generuje informacje o debugowaniu i umieść go w bazie danych programu (plik PDB). Określanie `-`, która jest włączona, jeśli nie określisz **/debug**, powoduje, że żadne informacje o debugowaniu ma zostać utworzony.  
  
 `full` &#124; `pdbonly`  
 Określa typ informacji dotyczących debugowania generowanych przez kompilator. Pełna argumentu, który jest efektu, jeśli nie określisz **/debug:pdbonly**, umożliwia dołączenie debugera do działającego programu. Określenie pdbonly umożliwia debugowanie, gdy program jest uruchamiany w debugerze, ale będą wyświetlane tylko asemblera jeśli uruchomiony program jest podłączony do debugera kodu źródłowego.  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja służy do tworzenia kompilacji do debugowania. Jeśli **/debug**, **/debug+**, lub **/debug:full** nie zostanie określony, nie można debugować pliku wyjściowego z programu.  
  
 Jeśli używasz **/debug:full**, należy pamiętać, że niektóre wpływa na szybkość i rozmiar JIT zoptymalizowany kod i mały wpływ na jakości kodu z **/debug:full**. Firma Microsoft zaleca **/debug:pdbonly** lub nie pliku PDB generowania wersji kodu.  
  
> [!NOTE]
>  Jeden różnica między **/debug:pdbonly** i **/debug:full** jest to, że z **/debug:full** kompilator emituje <xref:System.Diagnostics.DebuggableAttribute>, które są używane do Poinformuj kompilator JIT te informacje debugowania są dostępne. W związku z tym będzie wyświetlany komunikat o błędzie, jeśli kod zawiera <xref:System.Diagnostics.DebuggableAttribute> ustawiona na wartość false, jeśli używasz **/debug:full**.  
  
 Aby uzyskać więcej informacji na temat konfigurowania wydajność debugowania aplikacji, zobacz [ułatwiając obraz do debugowania](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Aby zmienić lokalizację pliku .pdb, zobacz [/PDB (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **informacje o debugowaniu** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Przykład  
 Umieść informacje o debugowaniu w pliku wyjściowym `app.pdb`:  
  
```console  
csc /debug /pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
