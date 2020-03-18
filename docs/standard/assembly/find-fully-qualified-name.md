---
title: 'Jak: Znajdź w pełni kwalifikowaną nazwę zestawu'
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 49ebaeabee7a346fb84f09e5a9e34590d1ea9811
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "74348195"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a>Jak: Znajdź w pełni kwalifikowaną nazwę zestawu

Aby odkryć w pełni kwalifikowaną nazwę zestawu .NET Framework w globalnej pamięci podręcznej zestawów, użyj narzędzia Global Assembly Cache tool[(Gacutil.exe).](../../framework/tools/gacutil-exe-gac-tool.md) Zobacz [jak: Wyświetlanie zawartości globalnej pamięci podręcznej zestawów](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).

W przypadku zestawów .NET Core i zestawów .NET Framework, które nie są w globalnej pamięci podręcznej zestawów, można uzyskać w pełni kwalifikowaną nazwę zestawu na wiele sposobów:

- Kod służy do danych wyjściowych informacji do konsoli lub zmiennej lub można użyć [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) do zbadania metadanych zestawu, który zawiera w pełni kwalifikowaną nazwę.

- Jeśli zestaw jest już załadowany przez aplikację, można <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> pobrać wartość właściwości, aby uzyskać w pełni kwalifikowaną nazwę. Można użyć <xref:System.Type.Assembly> właściwości zdefiniowanew <xref:System.Type> tym zestawie, aby pobrać <xref:System.Reflection.Assembly> odwołanie do obiektu. Przykład stanowi ilustrację.

- Jeśli znasz ścieżkę systemu plików zestawu, `static` można wywołać `Shared` (C#) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> lub (Visual Basic) metoda, aby uzyskać w pełni kwalifikowaną nazwę zestawu. Poniżej przedstawiono prosty przykład.

  ```csharp
  using System;
  using System.Reflection;

  public class Example
  {
     public static void Main()
     {
        Console.WriteLine(AssemblyName.GetAssemblyName(@".\UtilityLibrary.dll"));
     }
  }
  // The example displays output like the following:
  //   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

  ```vb
  Imports System.Reflection

  Public Module Example
     Public Sub Main
        Console.WriteLine(AssemblyName.GetAssemblyName(".\UtilityLibrary.dll"))
     End Sub
  End Module
  ' The example displays output like the following:
  '   UtilityLibrary, Version=1.1.0.0, Culture=neutral, PublicKeyToken=null
  ```

- Za pomocą [ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) można zbadać metadane zestawu, który zawiera w pełni kwalifikowaną nazwę.

Aby uzyskać więcej informacji na temat ustawiania atrybutów zestawu, takich jak wersja, kultura i nazwa zestawu, zobacz [Ustawianie atrybutów zestawu](set-attributes.md). Aby uzyskać więcej informacji na temat nadawania zestawowi silnej nazwy, zobacz [Tworzenie i używanie zestawów o silnych nazwach](create-use-strong-named.md).

## <a name="example"></a>Przykład

W poniższym przykładzie pokazano, jak wyświetlić w pełni kwalifikowaną nazwę zestawu zawierającego określoną klasę do konsoli. Używa <xref:System.Type.Assembly?displayProperty=nameWithType> właściwości, aby pobrać odwołanie do zestawu z typu, który jest zdefiniowany w tym zestawie.

```cpp
#using <System.dll>
#using <System.Data.dll>

using namespace System;
using namespace System::Reflection;

ref class asmname
{
public:
    static void Main()
    {
        Type^ t = System::Data::DataSet::typeid;
        String^ s = t->Assembly->FullName->ToString();
        Console::WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
};

int main()
{
    asmname::Main();
}
```

```csharp
using System;
using System.Reflection;

class asmname
{
    public static void Main()
    {
        Type t = typeof(System.Data.DataSet);
        string s = t.Assembly.FullName.ToString();
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s);
    }
}
```

```vb
Imports System.Reflection

Class asmname
    Public Shared Sub Main()
        Dim t As Type = GetType(System.Data.DataSet)
        Dim s As String = t.Assembly.FullName.ToString()
        Console.WriteLine("The fully qualified assembly name " +
            "containing the specified class is {0}.", s)
    End Sub
End Class
```

## <a name="see-also"></a>Zobacz też

- [Nazwy zestawów](names.md)
- [Tworzenie zestawów](create.md)
- [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md)
- [Globalna pamięć podręczna zestawów](../../framework/app-domains/gac.md)
- [Jak program runtime lokalizuje zestawy](../../framework/deployment/how-the-runtime-locates-assemblies.md)
