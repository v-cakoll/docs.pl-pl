---
title: -linkresource (opcje kompilatora C#)
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
ms.openlocfilehash: feca4713fe0e704799e2abbae3818edd0f3a5c84
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523178"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (opcje kompilatora C#)
Tworzy łącze do zasobów .NET Framework w pliku wyjściowym. Plik zasobu nie zostanie dodany do pliku wyjściowego. To różni się od [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) opcję, która osadzić pliku zasobów w pliku wyjściowym.  
  
## <a name="syntax"></a>Składnia  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Argumenty  
 `filename`  
 Plik zasobów .NET Framework, z którym chcesz się połączyć z zestawu.  
  
 `identifier` (opcjonalnie)  
 Nazwa logiczna zasobu; Nazwa która jest używana do ładowania zasobów. Wartość domyślna to nazwa pliku.  
  
 `accessibility-modifier` (opcjonalnie)  
 Dostępność zasobów: publicznych lub prywatnych. Wartość domyślna jest publiczny.  
  
## <a name="remarks"></a>Uwagi  
 Połączone zasoby są domyślnie publiczne w zestawie podczas ich tworzenia za pomocą kompilatora C#. Zasoby prywatne, ustaw `private` jako modyfikator dostępności metody dostępu. Nie inne modyfikator innych niż `public` lub `private` jest dozwolone.  
  
 **-linkresource —** wymaga jednej z [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) opcji innych niż **-target: module**.  
  
 Jeśli `filename` jest plikiem zasobów .NET Framework, utworzonym na przykład przez [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) lub w środowisku deweloperskim, jest dostępny za pomocą elementów członkowskich w <xref:System.Resources> przestrzeni nazw. Aby uzyskać więcej informacji, zobacz <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. W przypadku wszystkich innych zasobów, użyj `GetManifestResource` metody <xref:System.Reflection.Assembly> klasy, aby uzyskać dostęp do zasobu w czasie wykonywania.  
  
 Plik określony w `filename` może być dowolnym formacie. Na przykład można wprowadzić natywną DLL częścią zestawu, dzięki czemu mogą być zainstalowane w globalnej pamięci podręcznej i dostępne z kodu zarządzanego w zestawie. Drugi poniższych przykładach pokazano, jak to zrobić. Możesz zrobić to samo w Assembly Linker. Trzeci poniższych przykładach pokazano, jak to zrobić. Aby uzyskać więcej informacji, zobacz [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) i [Praca z zestawami i Global Assembly Cache](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** jest krótka forma **- linkresource —**.  
  
 Ta opcja kompilatora jest niedostępna w programie Visual Studio i nie można zmienić programowo.  
  
## <a name="example"></a>Przykład  
 Skompilować `in.cs` i link do pliku zasobów `rf.resource`:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Przykład  
 Skompilować `A.cs` do biblioteki DLL, łącze macierzystego N.dll biblioteki DLL, a następnie umieścić dane wyjściowe w globalnej pamięci podręcznej zestawów (GAC). W tym przykładzie A.dll i N.dll będą znajdować się w pamięci podręcznej GAC.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Przykład  
 Ten przykład działa tak samo jak poprzedni, ale przy użyciu opcji Assembly Linker.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Zobacz też  

- [Opcje kompilatora C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Al.exe (konsolidator zestawów)](../../../framework/tools/al-exe-assembly-linker.md)  
- [Praca z zestawami i globalną pamięcią podręczną zestawów](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
- [Zarządzanie właściwościami projektu i rozwiązania](/visualstudio/ide/managing-project-and-solution-properties)
