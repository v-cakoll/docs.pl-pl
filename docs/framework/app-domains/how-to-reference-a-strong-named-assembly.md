---
title: 'Instrukcje: Odwołanie do zestawu o silnej nazwie'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- strong-named assemblies, compile-time references
- compile-time assembly referencing
- assemblies [.NET Framework], strong-named
- assembly binding, strong-named
ms.assetid: 4c6a406a-b5eb-44fa-b4ed-4e95bb95a813
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 080d05a27b9e0b6ad4ff52d67ef8d9209dc1c697
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927955"
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="d40cb-102">Instrukcje: Odwołanie do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="d40cb-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="d40cb-103">Proces odwoływania się do typów lub zasobów w zestawie o silnej nazwie jest zwykle niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="d40cb-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="d40cb-104">Odwołanie można wykonać w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="d40cb-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="d40cb-105">Odwołanie w czasie kompilacji odbywa się po wskazaniu kompilatora, który zestaw jawnie odwołuje się do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="d40cb-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="d40cb-106">W przypadku korzystania z odwołania w czasie kompilacji kompilator automatycznie pobiera klucz publiczny do określonego zestawu o silnej nazwie i umieszcza go w odwołaniu do zestawu, który jest kompilowany.</span><span class="sxs-lookup"><span data-stu-id="d40cb-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d40cb-107">Zestaw o silnej nazwie może używać tylko typów z innych zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="d40cb-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="d40cb-108">W przeciwnym razie zabezpieczenia zestawu o silnej nazwie byłyby naruszone.</span><span class="sxs-lookup"><span data-stu-id="d40cb-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="d40cb-109">Aby wykonać odwołanie do zestawu o silnej nazwie w czasie kompilacji</span><span class="sxs-lookup"><span data-stu-id="d40cb-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="d40cb-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="d40cb-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="d40cb-111">\<*Kompilator polecenia*>  **/Reference:** \<*Nazwa zestawu*></span><span class="sxs-lookup"><span data-stu-id="d40cb-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="d40cb-112">W tym poleceniu *kompilator* jest poleceniem kompilatora dla używanego języka, a *Nazwa zestawu* to nazwa zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d40cb-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="d40cb-113">Można również użyć innych opcji kompilatora, takich jak opcja **/t: Library** do tworzenia zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="d40cb-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="d40cb-114">Poniższy przykład tworzy zestaw o nazwie `myAssembly.dll` , który odwołuje się do zestawu o silnej nazwie wywołanego `myLibAssembly.dll` z `myAssembly.cs`modułu kodu o nazwie.</span><span class="sxs-lookup"><span data-stu-id="d40cb-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="d40cb-115">Aby wprowadzić odwołanie w czasie wykonywania do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="d40cb-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1. <span data-ttu-id="d40cb-116">Podczas wykonywania odwołania do zestawu o silnej nazwie (na przykład przy użyciu <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> ), należy użyć nazwy wyświetlanej zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="d40cb-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="d40cb-117">Składnia nazwy wyświetlanej jest następująca:</span><span class="sxs-lookup"><span data-stu-id="d40cb-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="d40cb-118">\<*Nazwa* zestawu,\< *numer wersji,* kultura, token klucza publicznego \<> \<>>></span><span class="sxs-lookup"><span data-stu-id="d40cb-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="d40cb-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d40cb-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="d40cb-120">W tym przykładzie `PublicKeyToken` jest to szesnastkowa postać tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="d40cb-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="d40cb-121">Jeśli nie ma żadnej wartości kulturowej, `Culture=neutral`Użyj.</span><span class="sxs-lookup"><span data-stu-id="d40cb-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="d40cb-122">Poniższy przykład kodu pokazuje, <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> jak używać tych informacji przy użyciu metody.</span><span class="sxs-lookup"><span data-stu-id="d40cb-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="d40cb-123">Można wydrukować format szesnastkowy klucza publicznego i tokenu klucza publicznego dla określonego zestawu za pomocą następującego polecenia [silnej nazwy (SN. exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) :</span><span class="sxs-lookup"><span data-stu-id="d40cb-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="d40cb-124">**SN — zestaw \< TP** **>**</span><span class="sxs-lookup"><span data-stu-id="d40cb-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="d40cb-125">Jeśli masz plik klucza publicznego, możesz użyć poniższego polecenia (należy zwrócić uwagę na różnice w przypadku opcji wiersza polecenia):</span><span class="sxs-lookup"><span data-stu-id="d40cb-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="d40cb-126">**SN-TP \< —** *plik klucza publicznego* **>**</span><span class="sxs-lookup"><span data-stu-id="d40cb-126">**sn -tp \<** *public key file* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d40cb-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="d40cb-127">See also</span></span>

- [<span data-ttu-id="d40cb-128">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="d40cb-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
