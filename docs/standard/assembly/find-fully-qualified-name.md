---
title: 'Instrukcje: Znajdowanie w pełni kwalifikowanej nazwy zestawu'
ms.date: 08/20/2019
helpviewer_keywords:
- names [.NET Framework], fully qualified type names
- names [.NET Framework], assemblies
- assemblies [.NET Framework], names
ms.assetid: 009dae23-e1f6-4a64-9a9a-32e4c34802b0
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 4fc670adc80a6f4ce7b36074185dcd3bb85fbc67
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70991310"
---
# <a name="how-to-find-an-assemblys-fully-qualified-name"></a><span data-ttu-id="6844c-102">Instrukcje: Znajdowanie w pełni kwalifikowanej nazwy zestawu</span><span class="sxs-lookup"><span data-stu-id="6844c-102">How to: Find an assembly's fully qualified name</span></span>

<span data-ttu-id="6844c-103">Aby odnaleźć w pełni kwalifikowaną nazwę zestawu .NET Framework w globalnej pamięci podręcznej zestawów, użyj narzędzia globalnej pamięci podręcznej zestawów ([Gacutil. exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span><span class="sxs-lookup"><span data-stu-id="6844c-103">To discover the fully qualified name of a .NET Framework assembly in the global assembly cache, use the Global Assembly Cache tool ([Gacutil.exe](../../framework/tools/gacutil-exe-gac-tool.md)).</span></span> <span data-ttu-id="6844c-104">Zobacz [How to: Wyświetl zawartość globalnej pamięci podręcznej](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md)zestawów.</span><span class="sxs-lookup"><span data-stu-id="6844c-104">See [How to: View the contents of the global assembly cache](../../framework/app-domains/how-to-view-the-contents-of-the-gac.md).</span></span>

<span data-ttu-id="6844c-105">W przypadku zestawów .NET Core i dla zestawów .NET Framework, które nie znajdują się w globalnej pamięci podręcznej zestawów, można uzyskać w pełni kwalifikowaną nazwę zestawu na wiele sposobów:</span><span class="sxs-lookup"><span data-stu-id="6844c-105">For .NET Core assemblies, and for .NET Framework assemblies that aren't in the global assembly cache, you can get the fully qualified assembly name in a number of ways:</span></span>

- <span data-ttu-id="6844c-106">Można użyć kodu do wyprowadzania informacji do konsoli lub do zmiennej lub użyć [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md) do sprawdzenia metadanych zestawu, który zawiera w pełni kwalifikowaną nazwę.</span><span class="sxs-lookup"><span data-stu-id="6844c-106">You can use code to output the information to the console or to a variable, or you can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

- <span data-ttu-id="6844c-107">Jeśli zestaw jest już załadowany przez aplikację, możesz pobrać wartość <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> właściwości, aby uzyskać w pełni kwalifikowaną nazwę.</span><span class="sxs-lookup"><span data-stu-id="6844c-107">If the assembly is already loaded by the application, you can retrieve the value of the <xref:System.Reflection.Assembly.FullName%2A?displayProperty=nameWithType> property to get the fully qualified name.</span></span> <span data-ttu-id="6844c-108">Możesz użyć <xref:System.Type.Assembly> właściwości <xref:System.Type> zdefiniowanej w tym zestawie, aby <xref:System.Reflection.Assembly> pobrać odwołanie do obiektu.</span><span class="sxs-lookup"><span data-stu-id="6844c-108">You can use the <xref:System.Type.Assembly> property of a <xref:System.Type> defined in that assembly to retrieve a reference to the <xref:System.Reflection.Assembly> object.</span></span> <span data-ttu-id="6844c-109">Przykład stanowi ilustrację.</span><span class="sxs-lookup"><span data-stu-id="6844c-109">The example provides an illustration.</span></span>

- <span data-ttu-id="6844c-110">Jeśli znasz ścieżkę systemu plików zestawu `static` , możesz wywołać metodę (C#) lub `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> , aby uzyskać w pełni kwalifikowaną nazwę zestawu.</span><span class="sxs-lookup"><span data-stu-id="6844c-110">If you know the assembly's file system path, you can call the `static` (C#) or `Shared` (Visual Basic) <xref:System.Reflection.AssemblyName.GetAssemblyName%2A?displayProperty=nameWithType> method to get the fully qualified assembly name.</span></span> <span data-ttu-id="6844c-111">Poniżej przedstawiono prosty przykład.</span><span class="sxs-lookup"><span data-stu-id="6844c-111">The following is a simple example.</span></span>

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

- <span data-ttu-id="6844c-112">Do sprawdzenia metadanych zestawu, który zawiera w pełni kwalifikowaną nazwę, można użyć [Ildasm. exe (Il dezasembler)](../../framework/tools/ildasm-exe-il-disassembler.md) .</span><span class="sxs-lookup"><span data-stu-id="6844c-112">You can use the [Ildasm.exe (IL Disassembler)](../../framework/tools/ildasm-exe-il-disassembler.md) to examine the assembly's metadata, which contains the fully qualified name.</span></span>

<span data-ttu-id="6844c-113">Aby uzyskać więcej informacji na temat ustawiania atrybutów zestawu, takich jak wersja, kultura i nazwa zestawu, zobacz [Ustawianie atrybutów zestawu](set-attributes.md).</span><span class="sxs-lookup"><span data-stu-id="6844c-113">For more information about setting assembly attributes such as version, culture, and assembly name, see [Set assembly attributes](set-attributes.md).</span></span> <span data-ttu-id="6844c-114">Aby uzyskać więcej informacji na temat nadawania silnej nazwy zestawu, zobacz [Tworzenie i używanie zestawów o silnej nazwie](create-use-strong-named.md).</span><span class="sxs-lookup"><span data-stu-id="6844c-114">For more information about giving an assembly a strong name, see [Create and use strong-named assemblies](create-use-strong-named.md).</span></span>

## <a name="example"></a><span data-ttu-id="6844c-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="6844c-115">Example</span></span>

<span data-ttu-id="6844c-116">Poniższy przykład pokazuje, jak wyświetlić w pełni kwalifikowaną nazwę zestawu zawierającego określoną klasę w konsoli programu.</span><span class="sxs-lookup"><span data-stu-id="6844c-116">The following example shows how to display the fully qualified name of an assembly containing a specified class to the console.</span></span> <span data-ttu-id="6844c-117">Używa <xref:System.Type.Assembly?displayProperty=nameWithType> właściwości, aby pobrać odwołanie do zestawu z typu, który jest zdefiniowany w tym zestawie.</span><span class="sxs-lookup"><span data-stu-id="6844c-117">It uses the <xref:System.Type.Assembly?displayProperty=nameWithType> property to retrieve a reference to an assembly from a type that's defined in that assembly.</span></span>

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
Imports System
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

## <a name="see-also"></a><span data-ttu-id="6844c-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6844c-118">See also</span></span>

- [<span data-ttu-id="6844c-119">Nazwy zestawów</span><span class="sxs-lookup"><span data-stu-id="6844c-119">Assembly names</span></span>](names.md)
- [<span data-ttu-id="6844c-120">Tworzenie zestawów</span><span class="sxs-lookup"><span data-stu-id="6844c-120">Create assemblies</span></span>](create.md)
- [<span data-ttu-id="6844c-121">Tworzenie i używanie zestawów o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="6844c-121">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
- [<span data-ttu-id="6844c-122">Globalna pamięć podręczna zestawów</span><span class="sxs-lookup"><span data-stu-id="6844c-122">Global assembly cache</span></span>](../../framework/app-domains/gac.md)
- [<span data-ttu-id="6844c-123">Jak środowisko uruchomieniowe lokalizuje zestawy</span><span class="sxs-lookup"><span data-stu-id="6844c-123">How the runtime locates assemblies</span></span>](../../framework/deployment/how-the-runtime-locates-assemblies.md)
- [<span data-ttu-id="6844c-124">Program z zestawami</span><span class="sxs-lookup"><span data-stu-id="6844c-124">Program with assemblies</span></span>](program.md)