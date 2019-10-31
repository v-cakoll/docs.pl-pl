---
title: 'Instrukcje: odwoływanie się do zestawu o silnej nazwie'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 427550e1fbeb38cefbb4afe97d80e198ac2d6cb0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73127633"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="79b37-102">Instrukcje: odwoływanie się do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="79b37-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="79b37-103">Proces odwoływania się do typów lub zasobów w zestawie o silnej nazwie jest zwykle niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="79b37-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="79b37-104">Odwołanie można wykonać w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="79b37-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="79b37-105">Odwołanie w czasie kompilacji odbywa się po wskazaniu kompilatora, który zestaw ma zostać skompilowany jawnie odwołuje się do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="79b37-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="79b37-106">W przypadku korzystania z odwołania w czasie kompilacji kompilator automatycznie pobiera klucz publiczny do określonego zestawu o silnej nazwie i umieszcza go w odwołaniu do zestawu, który jest kompilowany.</span><span class="sxs-lookup"><span data-stu-id="79b37-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="79b37-107">Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="79b37-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="79b37-108">W przeciwnym razie zabezpieczenia zestawu o silnej nazwie byłyby naruszone.</span><span class="sxs-lookup"><span data-stu-id="79b37-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="79b37-109">Utwórz odwołanie w czasie kompilacji do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="79b37-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="79b37-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="79b37-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="79b37-111">\<*polecenia kompilatora*>  **/Reference:** \<*Nazwa zestawu*></span><span class="sxs-lookup"><span data-stu-id="79b37-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="79b37-112">W tym poleceniu *kompilator* jest poleceniem kompilatora dla używanego języka, a *Nazwa zestawu* to nazwa zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="79b37-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="79b37-113">Można również użyć innych opcji kompilatora, takich jak opcja **/t: Library** do tworzenia zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="79b37-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="79b37-114">Poniższy przykład tworzy zestaw o nazwie Moja *Assembly. dll* , który odwołuje się do zestawu o silnej nazwie o nazwie *myLibAssembly. dll* z modułu kodu o nazwie *myAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="79b37-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="79b37-115">Utwórz odwołanie w czasie wykonywania do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="79b37-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="79b37-116">Po wprowadzeniu odwołania w czasie wykonywania do zestawu o silnej nazwie, na przykład przy użyciu metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType>, należy użyć nazwy wyświetlanej zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="79b37-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="79b37-117">Składnia nazwy wyświetlanej jest następująca:</span><span class="sxs-lookup"><span data-stu-id="79b37-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="79b37-118">\<*nazwę zestawu*> **,** \<*numer wersji*> **,** \<>*kulturowe* **,** \<*token klucza publicznego*></span><span class="sxs-lookup"><span data-stu-id="79b37-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="79b37-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="79b37-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
```  

<span data-ttu-id="79b37-120">W tym przykładzie `PublicKeyToken` jest szesnastkową formą tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="79b37-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="79b37-121">Jeśli nie ma żadnej wartości kulturowej, użyj `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="79b37-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="79b37-122">Poniższy przykład kodu pokazuje, jak używać tych informacji przy użyciu metody <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="79b37-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

```cpp
Assembly^ myDll =
    Assembly::Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```csharp
Assembly myDll =
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1");
```

```vb
Dim myDll As Assembly = _
    Assembly.Load("myDll, Version=1.0.0.1, Culture=neutral, PublicKeyToken=9b35aa32c18d4fb1")
```

<span data-ttu-id="79b37-123">Można wydrukować format szesnastkowy klucza publicznego i tokenu klucza publicznego dla określonego zestawu za pomocą następującego polecenia [silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="79b37-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="79b37-124">**SN-Tp \<** *zestawu* **>**</span><span class="sxs-lookup"><span data-stu-id="79b37-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="79b37-125">Jeśli masz plik klucza publicznego, możesz użyć poniższego polecenia (należy zwrócić uwagę na różnice w przypadku opcji wiersza polecenia):</span><span class="sxs-lookup"><span data-stu-id="79b37-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="79b37-126">**SN-tp \<** *pliku klucza publicznego* **>**</span><span class="sxs-lookup"><span data-stu-id="79b37-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="79b37-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="79b37-127">See also</span></span>

- [<span data-ttu-id="79b37-128">Tworzenie i używanie zestawów o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="79b37-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
