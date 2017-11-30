---
title: -out (opcje kompilatora C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: "15"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 332e369b6fe2de79c9063daa9e6d5c0e83f0bcc8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="out-c-compiler-options"></a>/out (opcje kompilatora C#)
**/Out** opcji określa nazwę pliku wyjściowego.  
  
## <a name="syntax"></a>Składnia  
  
```console  
/out:filename  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Nazwa pliku wyjściowego, utworzony przez kompilator.  
  
## <a name="remarks"></a>Uwagi  
 W wierszu polecenia jest można określić wielu plików wyjściowych dla Twojego kompilacji. Kompilator oczekuje można znaleźć plików kodu co najmniej jednego źródłowego po **/out** opcji. Następnie zostanie skompilowany wszystkich plików kodu źródłowego w określony przez to plik wyjściowy **/out** opcji.  
  
 Określ pełną nazwę i rozszerzenie pliku, który chcesz utworzyć.  
  
 Jeśli nie określisz nazwy pliku wyjściowego:  
  
-   .exe potrwa nazwy z pliku kodu źródłowego, który zawiera **Main** metody.  
  
-   .Dll lub moduł .netmodule potrwa nazwy z pierwszego pliku kodu źródłowego.  
  
 Używana do kompilowania jednego pliku wyjściowego pliku kodu źródłowego nie można użyć w tej samej kompilacji dla kompilacji innego pliku wyjściowego.  
  
 Podczas tworzenia wielu plików wyjściowych w kompilacji wiersza polecenia, należy pamiętać, tylko jeden z plików wyjściowych może być zestawu i określonej tylko pierwszy plik wyjściowy (jawnie ani niejawnie z **/out**) może być zestawu .  
  
 Wszystkie moduły utworzone jako część kompilacji stają się pliki skojarzone z dowolnego zestawu również utworzone w kompilacji. Użyj [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) Aby wyświetlić manifest zestawu, aby wyświetlić skojarzone pliki.  
  
 / Out — opcja kompilatora jest wymagane dla pliku exe celem przyjaznego zestawu. Aby uzyskać więcej informacji, zobacz [przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Aby ustawić tę opcję kompilatora w środowisku programowania Visual Studio  
  
1.  Otwórz projekt **właściwości** strony.  
  
2.  Kliknij przycisk **aplikacji** strony właściwości.  
  
3.  Modyfikowanie **nazwy zestawu** właściwości.  
  
     Aby ustawić tę opcję kompilatora programowo: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> jest właściwością tylko do odczytu, który jest określany przez kombinację typu projektu (exe, biblioteki i tak dalej) i nazwy zestawu. Modyfikowanie jedną lub obie te właściwości będą należy ustawić nazwę pliku wyjściowego.  
  
## <a name="example"></a>Przykład  
 Kompiluj `t.cs` i utworzyć pliku wyjściowego `t.exe`, a także kompilacji `t2.cs` i utworzyć pliku wyjściowego modułu `mymodule.netmodule`:  
  
```console  
csc t.cs /out:mymodule.netmodule /target:module t2.cs  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Przyjazne zestawy](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
