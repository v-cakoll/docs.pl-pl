---
title: -debug (opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /debug
helpviewer_keywords:
- debug compiler option [C#]
- -debug compiler option [C#]
- /debug compiler option [C#]
ms.assetid: e2b48c07-01bc-45cc-a52c-92e9085eb969
ms.openlocfilehash: ab9b299579f9ab4a854ce7ab220edc87e0c66745
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="-debug-c-compiler-options"></a>-debug (opcje kompilatora C#)
**-Debug** opcji powoduje, że kompilator generuje informacje o debugowaniu i umieścić go w pliku danych wyjściowych.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-debug[+ | -]  
-debug:{full | pdbonly}  
```  
  
## <a name="arguments"></a>Argumenty  
 `+` &#124; `-`  
 Określanie `+`, lub po prostu **-debug**, powoduje, że kompilator generuje informacje o debugowaniu i umieść go w bazie danych programu (plik PDB). Określanie `-`, która jest włączona, jeśli nie określisz **-debug**, powoduje, że żadne informacje o debugowaniu ma zostać utworzony.  
  
 `full` &#124; `pdbonly`  
 Określa typ informacji dotyczących debugowania generowanych przez kompilator. Pełna argumentu, który jest efektu, jeśli nie określisz **-debugowania: pdbonly**, umożliwia dołączenie debugera do działającego programu. Określenie pdbonly umożliwia debugowanie, gdy program jest uruchamiany w debugerze, ale będą wyświetlane tylko asemblera jeśli uruchomiony program jest podłączony do debugera kodu źródłowego.  
  
## <a name="remarks"></a>Uwagi  
 Ta opcja służy do tworzenia kompilacji do debugowania. Jeśli **-debug**, **-debugowania +**, lub **-debugowania: full** nie zostanie określony, nie można debugować pliku wyjściowego z programu.  
  
 Jeśli używasz **-debugowania: full**, należy pamiętać, że niektóre wpływa na szybkość i rozmiar JIT zoptymalizowany kod i mały wpływ na jakości kodu z **-debugowania: full**. Firma Microsoft zaleca **-debugowania: pdbonly** lub nie pliku PDB generowania wersji kodu.  
  
> [!NOTE]
>  Jeden różnica między **-debugowania: pdbonly** i **-debugowania: full** jest to, że z **-debugowania: full** kompilator emituje <xref:System.Diagnostics.DebuggableAttribute>, używany do Poinformuj kompilator JIT te informacje debugowania są dostępne. W związku z tym będzie wyświetlany komunikat o błędzie, jeśli kod zawiera <xref:System.Diagnostics.DebuggableAttribute> ustawiona na wartość false, jeśli używasz **-debugowania: full**.  
  
 Aby uzyskać więcej informacji na temat konfigurowania wydajność debugowania aplikacji, zobacz [ułatwiając obraz do debugowania](../../../framework/debug-trace-profile/making-an-image-easier-to-debug.md).  
  
 Aby zmienić lokalizację pliku .pdb, zobacz [- pdb (opcje kompilatora C#)](../../../csharp/language-reference/compiler-options/pdb-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **kompilacji** strony właściwości.  
  
3.  Kliknij przycisk **zaawansowane** przycisku.  
  
4.  Modyfikowanie **informacje o debugowaniu** właściwości.  
  
 Aby uzyskać informacje dotyczące ustawiania tej opcji kompilatora programowo, zobacz <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DebugSymbols%2A>.  
  
## <a name="example"></a>Przykład  
 Umieść informacje o debugowaniu w pliku wyjściowym `app.pdb`:  
  
```console  
csc -debug -pdb:app.pdb test.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
