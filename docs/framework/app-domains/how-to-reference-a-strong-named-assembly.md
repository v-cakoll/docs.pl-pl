---
title: "Porady: odwołanie do zestawu o silnej nazwie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-bcl
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: b005926f99b7c151e5916a95a9852dd8b448a928
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-reference-a-strong-named-assembly"></a><span data-ttu-id="44af6-102">Porady: odwołanie do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="44af6-102">How to: Reference a Strong-Named Assembly</span></span>
<span data-ttu-id="44af6-103">Proces odwołania do typów lub zasoby zestawu z silną nazwą jest zazwyczaj niewidoczny.</span><span class="sxs-lookup"><span data-stu-id="44af6-103">The process for referencing types or resources in a strong-named assembly is usually transparent.</span></span> <span data-ttu-id="44af6-104">Istnieje możliwość odwołania w czasie kompilacji (wczesne wiązanie) lub w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="44af6-104">You can make the reference either at compile time (early binding) or at run time.</span></span>  
  
 <span data-ttu-id="44af6-105">Odwołanie kompilacji występuje, gdy w kompilatorze wskazaniu, że używanemu zestawowi jawnie odwoływać się do innego zestawu.</span><span class="sxs-lookup"><span data-stu-id="44af6-105">A compile-time reference occurs when you indicate to the compiler that your assembly explicitly references another assembly.</span></span> <span data-ttu-id="44af6-106">Korzystając z odwołujące się do kompilacji, kompilator automatycznie pobiera klucz publiczny docelowego zestawu o silnej nazwie i umieszcza je w odwołaniu do zestawu jest kompilowane zestawu.</span><span class="sxs-lookup"><span data-stu-id="44af6-106">When you use compile-time referencing, the compiler automatically gets the public key of the targeted strong-named assembly and places it in the assembly reference of the assembly being compiled.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="44af6-107">Zestaw o silnej nazwie można używać tylko typów od innych zestawów o silnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="44af6-107">A strong-named assembly can only use types from other strong-named assemblies.</span></span> <span data-ttu-id="44af6-108">W przeciwnym razie będzie naruszenia zabezpieczeń zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="44af6-108">Otherwise, the security of the strong-named assembly would be compromised.</span></span>  
  
### <a name="to-make-a-compile-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="44af6-109">Kompilacji odwołać się do zestawu o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="44af6-109">To make a compile-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="44af6-110">W wierszu polecenia wpisz następujące polecenie:</span><span class="sxs-lookup"><span data-stu-id="44af6-110">At the command prompt, type the following command:</span></span>  
  
     <span data-ttu-id="44af6-111">\<*polecenie kompilatora*> **/reference:**\<*nazwy zestawu*></span><span class="sxs-lookup"><span data-stu-id="44af6-111">\<*compiler command*> **/reference:**\<*assembly name*></span></span>  
  
     <span data-ttu-id="44af6-112">W tym poleceniu *polecenia kompilatora* polecenia kompilatora języka używasz, i *nazwy zestawu* jest nazwą jest odwołanie do zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="44af6-112">In this command, *compiler command* is the compiler command for the language you are using, and *assembly name* is the name of the strong-named assembly being referenced.</span></span> <span data-ttu-id="44af6-113">Umożliwia także inne opcje kompilatora, takich jak **Library** opcja do tworzenia zestawu biblioteki.</span><span class="sxs-lookup"><span data-stu-id="44af6-113">You can also use other compiler options, such as the **/t:library** option for creating a library assembly.</span></span>  
  
 <span data-ttu-id="44af6-114">Poniższy przykład tworzy zestaw o nazwie `myAssembly.dll` odwołuje się zestaw o silnej nazwie o nazwie `myLibAssembly.dll` z modułu kodu o nazwie `myAssembly.cs`.</span><span class="sxs-lookup"><span data-stu-id="44af6-114">The following example creates an assembly called `myAssembly.dll` that references a strong-named assembly called `myLibAssembly.dll` from a code module called `myAssembly.cs`.</span></span>  
  
```  
csc /t:library myAssembly.cs /reference:myLibAssembly.dll  
```  
  
### <a name="to-make-a-run-time-reference-to-a-strong-named-assembly"></a><span data-ttu-id="44af6-115">Do czasu wykonywania odwołać się do zestawu z silną nazwą</span><span class="sxs-lookup"><span data-stu-id="44af6-115">To make a run-time reference to a strong-named assembly</span></span>  
  
1.  <span data-ttu-id="44af6-116">Po dokonaniu środowiska wykonawczego odwołanie do zestawu z silną nazwą (na przykład za pomocą <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> lub <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> metodę), należy użyć nazwy wyświetlanej przywoływanego zestawu o silnej nazwie.</span><span class="sxs-lookup"><span data-stu-id="44af6-116">When you make a run-time reference to a strong-named assembly (for example, by using the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> or <xref:System.Reflection.Assembly.GetType%2A?displayProperty=nameWithType> method), you must use the display name of the referenced strong-named assembly.</span></span> <span data-ttu-id="44af6-117">Składnia nazwy wyświetlanej jest następujący:</span><span class="sxs-lookup"><span data-stu-id="44af6-117">The syntax of a display name is as follows:</span></span>  
  
     <span data-ttu-id="44af6-118">\<*Nazwa zestawu*>**,** \< *numer wersji*>**,** \<  *kultura*>**,** \< *token klucza publicznego*></span><span class="sxs-lookup"><span data-stu-id="44af6-118">\<*assembly name*>**,** \<*version number*>**,** \<*culture*>**,** \<*public key token*></span></span>  
  
     <span data-ttu-id="44af6-119">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="44af6-119">For example:</span></span>  
  
    ```  
    myDll, Version=1.1.0.0, Culture=en, PublicKeyToken=03689116d3a4ae33   
    ```  
  
     <span data-ttu-id="44af6-120">W tym przykładzie `PublicKeyToken` jest postaci szesnastkowej tokenu klucza publicznego.</span><span class="sxs-lookup"><span data-stu-id="44af6-120">In this example, `PublicKeyToken` is the hexadecimal form of the public key token.</span></span> <span data-ttu-id="44af6-121">Jeśli nie ma żadnej wartości kultury, użyj `Culture=neutral`.</span><span class="sxs-lookup"><span data-stu-id="44af6-121">If there is no culture value, use `Culture=neutral`.</span></span>  
  
 <span data-ttu-id="44af6-122">Poniższy przykład kodu pokazuje sposób używania tych informacji z <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> metody.</span><span class="sxs-lookup"><span data-stu-id="44af6-122">The following code example shows how to use this information with the <xref:System.Reflection.Assembly.Load%2A?displayProperty=nameWithType> method.</span></span>  
  
 [!code-cpp[Assembly.Load1#3](../../../samples/snippets/cpp/VS_Snippets_CLR/Assembly.Load1/CPP/load2.cpp#3)]
 [!code-csharp[Assembly.Load1#3](../../../samples/snippets/csharp/VS_Snippets_CLR/Assembly.Load1/CS/load2.cs#3)]
 [!code-vb[Assembly.Load1#3](../../../samples/snippets/visualbasic/VS_Snippets_CLR/Assembly.Load1/VB/load2.vb#3)]  
  
 <span data-ttu-id="44af6-123">Można drukować szesnastkowej klucz publiczny i token klucza publicznego dla określonego zestawu przy użyciu następujących [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) polecenia:</span><span class="sxs-lookup"><span data-stu-id="44af6-123">You can print the hexadecimal format of the public key and public key token for a specific assembly by using the following [Strong Name (Sn.exe)](../../../docs/framework/tools/sn-exe-strong-name-tool.md) command:</span></span>  
  
 <span data-ttu-id="44af6-124">**SN - Tp \<**  *zestawu***>**</span><span class="sxs-lookup"><span data-stu-id="44af6-124">**sn -Tp \<** *assembly* **>**</span></span>  
  
 <span data-ttu-id="44af6-125">Jeśli masz plik klucza publicznego, można użyć następującego polecenia (Uwaga różnica w przypadku opcji wiersza polecenia):</span><span class="sxs-lookup"><span data-stu-id="44af6-125">If you have a public key file, you can use the following command instead (note the difference in case on the command-line option):</span></span>  
  
 <span data-ttu-id="44af6-126">**SN - tp \<**  *zestawu***>**</span><span class="sxs-lookup"><span data-stu-id="44af6-126">**sn -tp \<** *assembly* **>**</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44af6-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="44af6-127">See Also</span></span>  
 [<span data-ttu-id="44af6-128">Tworzenie i używanie zestawów o silnej nazwie</span><span class="sxs-lookup"><span data-stu-id="44af6-128">Creating and Using Strong-Named Assemblies</span></span>](../../../docs/framework/app-domains/create-and-use-strong-named-assemblies.md)
