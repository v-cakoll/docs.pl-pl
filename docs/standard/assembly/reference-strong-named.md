---
title: 'Instrukcje: Odwołuje się do zestawu o silnej nazwie'
ms.date: 08/20/2019
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
dev_langs:
- csharp
- vb
- cpp
ms.openlocfilehash: 324cd42a2781202f19e7e1cb5055d571f0c58cf5
ms.sourcegitcommit: 7b1ce327e8c84f115f007be4728d29a89efe11ef
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2019
ms.locfileid: "70973132"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="f321e-102">Instrukcje: Odwołuje się do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="f321e-102">How to: Reference a strong-named assembly</span></span>
<span data-ttu-id="f321e-103">Proces odwoływania się do typów lub zasobów w zestawie o silnej nazwie jest zwykle niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="f321e-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="f321e-104">Odwołanie można wykonać w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="f321e-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
<span data-ttu-id="f321e-105">Odwołanie w czasie kompilacji odbywa się po wskazaniu kompilatora, który zestaw ma zostać skompilowany jawnie odwołuje się do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="f321e-105">A compile-time reference occurs when you indicate to the compiler that the assembly to be compiled explicitly references another assembly.</span></span> <span data-ttu-id="f321e-106">W przypadku korzystania z odwołania w czasie kompilacji kompilator automatycznie pobiera klucz publiczny do określonego zestawu o silnej nazwie i umieszcza go w odwołaniu do zestawu, który jest kompilowany.</span><span class="sxs-lookup"><span data-stu-id="f321e-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>
  
> [!NOTE]
> <span data-ttu-id="f321e-107">Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="f321e-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="f321e-108">W przeciwnym razie zabezpieczenia zestawu o silnej nazwie byłyby naruszone.</span><span class="sxs-lookup"><span data-stu-id="f321e-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
## <a name="make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="f321e-109">Utwórz odwołanie w czasie kompilacji do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="f321e-109">Make a compile-time reference to a strong-named assembly</span></span>  

<span data-ttu-id="f321e-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="f321e-110">At a command prompt, type the following command:</span></span>  

<span data-ttu-id="f321e-111">\<*Kompilator polecenia*>  **/Reference:** \<*Nazwa zestawu*></span><span class="sxs-lookup"><span data-stu-id="f321e-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  

<span data-ttu-id="f321e-112">W tym poleceniu *kompilator* jest poleceniem kompilatora dla używanego języka, a *Nazwa zestawu* to nazwa zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f321e-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="f321e-113">Można również użyć innych opcji kompilatora, takich jak opcja **/t: Library** do tworzenia zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="f321e-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  

<span data-ttu-id="f321e-114">Poniższy przykład tworzy zestaw o nazwie Moja *Assembly. dll* , który odwołuje się do zestawu o silnej nazwie o nazwie *myLibAssembly. dll* z modułu kodu o nazwie *myAssembly.cs*.</span><span class="sxs-lookup"><span data-stu-id="f321e-114">The following example creates an assembly called *myAssembly.dll* that references a strong-named assembly called *myLibAssembly.dll* from a code module called *myAssembly.cs*.</span></span>  

```cmd
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  

## <a name="make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="f321e-115">Utwórz odwołanie w czasie wykonywania do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="f321e-115">Make a run-time reference to a strong-named assembly</span></span>  
  
<span data-ttu-id="f321e-116">Podczas wykonywania odwołania do zestawu o silnej nazwie, na przykład przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> , należy użyć nazwy wyświetlanej zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f321e-116">When you make a run-time reference to a strong-named assembly, for example by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method, you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="f321e-117">Składnia nazwy wyświetlanej jest następująca:</span><span class="sxs-lookup"><span data-stu-id="f321e-117">The syntax of a display name is as follows:</span></span>  

<span data-ttu-id="f321e-118">\<*Nazwa* zestawu,\< *numer wersji,* kultura, token klucza publicznego \<> \<>>></span><span class="sxs-lookup"><span data-stu-id="f321e-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  

<span data-ttu-id="f321e-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f321e-119">For example:</span></span>  

```console
myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
```  

<span data-ttu-id="f321e-120">W tym przykładzie `PublicKeyToken` jest to szesnastkowa postać tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="f321e-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="f321e-121">Jeśli nie ma żadnej wartości kulturowej, `Culture=neutral`Użyj.</span><span class="sxs-lookup"><span data-stu-id="f321e-121">If there is no culture value, use `Culture=neutral`.</span></span>  

<span data-ttu-id="f321e-122">Poniższy przykład kodu pokazuje, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> jak używać tych informacji przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="f321e-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  

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

<span data-ttu-id="f321e-123">Można wydrukować format szesnastkowy klucza publicznego i tokenu klucza publicznego dla określonego zestawu za pomocą następującego polecenia [silnej nazwy (SN. exe)](../../framework/tools/sn-exe-strong-name-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="f321e-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  

<span data-ttu-id="f321e-124">**SN — zestaw \< TP** **>**</span><span class="sxs-lookup"><span data-stu-id="f321e-124">**sn -Tp \<** *assembly* **>**</span></span>  

<span data-ttu-id="f321e-125">Jeśli masz plik klucza publicznego, możesz użyć poniższego polecenia (należy zwrócić uwagę na różnice w przypadku opcji wiersza polecenia):</span><span class="sxs-lookup"><span data-stu-id="f321e-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  

<span data-ttu-id="f321e-126">**SN-TP \< —** *plik klucza publicznego* **>**</span><span class="sxs-lookup"><span data-stu-id="f321e-126">**sn -tp \<** *public key file* **>**</span></span>  

## <a name="see-also"></a><span data-ttu-id="f321e-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f321e-127">See also</span></span>

- [<span data-ttu-id="f321e-128">Tworzenie i używanie zestawów o silnych nazwach</span><span class="sxs-lookup"><span data-stu-id="f321e-128">Create and use strong-named assemblies</span></span>](create-use-strong-named.md)
