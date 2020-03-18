---
title: -linkresource (Opcje kompilatora C#)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: 41af8e0ba8ffebd07d3cb1d2bc5fbc04b8cd595d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79173734"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (Opcje kompilatora C#)
Tworzy łącze do zasobu .NET Framework w pliku wyjściowym. Plik zasobu nie jest dodawany do pliku wyjściowego. Różni się to od opcji [-resource,](./resource-compiler-option.md) która osadza plik zasobu w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobów .NET Framework, do którego chcesz połączyć się z zestawu.  
  
 `identifier` (opcjonalnie)  
 Logiczna nazwa zasobu; nazwa, która jest używana do ładowania zasobu. Wartością domyślną jest nazwa pliku.  
  
 `accessibility-modifier` (opcjonalnie)  
 Dostępność zasobu: publiczna lub prywatna. Wartość domyślna jest publiczna.  
  
## <a name="remarks"></a>Uwagi  
 Domyślnie połączone zasoby są publiczne w zestawie, gdy są tworzone za pomocą kompilatora C#. Aby zasoby były `private` prywatne, określ jako modyfikator ułatwień dostępu. Żaden inny modyfikator inny niż `public` lub `private` jest dozwolony.  
  
 **-linkresource** wymaga jednej z opcji [-target](./target-compiler-option.md) innych niż **-target:module**.  
  
 Jeśli `filename` jest plikiem zasobów .NET Framework utworzonym na przykład przez [resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku <xref:System.Resources> programistycznym, można uzyskać do niego dostęp za pomocą elementów członkowskich w obszarze nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Dla wszystkich innych zasobów `GetManifestResource` należy użyć <xref:System.Reflection.Assembly> metod w klasie, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 Plik określony w `filename` może być dowolny format. Na przykład można zrobić natywną część dll zestawu, dzięki czemu można zainstalować w globalnej pamięci podręcznej zestawów i uzyskać dostęp z kodu zarządzanego w zestawie. Drugi z poniższych przykładów pokazuje, jak to zrobić. To samo można zrobić w konsolidacie zestawu. Trzeci z poniższych przykładów pokazuje, jak to zrobić. Aby uzyskać więcej informacji, zobacz [Al.exe (Łączełączenie zestawów)](../../../framework/tools/al-exe-assembly-linker.md) i [praca z zespołami i globalną pamięcią podręczną zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** jest krótką formą **-linkresource**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można jej zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Kompilowanie `in.cs` i tworzenie `rf.resource`łącza do pliku zasobów:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Przykład  
 Skompiluj `A.cs` w dll, łącze do nll macierzystej dll dll i umieścić dane wyjściowe w globalnej pamięci podręcznej zestawów (GAC). W tym przykładzie zarówno A.dll, jak i N.dll będą dostępne w identyfikatorze GAC.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Przykład  
 W tym przykładzie robi to samo, co poprzedni, ale za pomocą opcji konsolidatora zestawów.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Zobacz też

- [Opcje kompilatora Języka C#](./index.md)
- [Al.exe (konsolidator zestawów)](../../../framework/tools/al-exe-assembly-linker.md)
- [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)
- [Zarządzanie właściwościami projektów i rozwiązań](/visualstudio/ide/managing-project-and-solution-properties)
