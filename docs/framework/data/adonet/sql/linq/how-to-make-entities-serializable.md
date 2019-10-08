---
title: 'Instrukcje: Tworzenie obiektów do serializacji'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 5e9d078ed2daacfa48b09693f533e9aade613281
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002714"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="c41ba-102">Instrukcje: Tworzenie obiektów do serializacji</span><span class="sxs-lookup"><span data-stu-id="c41ba-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="c41ba-103">Jednostki można serializować podczas generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="c41ba-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="c41ba-104">Klasy jednostek są uzupełnione atrybutem <xref:System.Runtime.Serialization.DataContractAttribute> i kolumnami z atrybutem <xref:System.Runtime.Serialization.DataMemberAttribute>.</span><span class="sxs-lookup"><span data-stu-id="c41ba-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="c41ba-105">Deweloperzy korzystający z programu Visual Studio mogą w tym celu używać Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="c41ba-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="c41ba-106">Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj opcji **/Serialization** z argumentem `unidirectional`.</span><span class="sxs-lookup"><span data-stu-id="c41ba-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="c41ba-107">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="c41ba-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c41ba-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="c41ba-108">Example</span></span>  
 <span data-ttu-id="c41ba-109">Następujące wiersze poleceń SQLMetal tworzą pliki, które mają możliwe do serializacji jednostki.</span><span class="sxs-lookup"><span data-stu-id="c41ba-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```console  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```console  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="c41ba-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c41ba-110">See also</span></span>

- [<span data-ttu-id="c41ba-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="c41ba-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="c41ba-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="c41ba-112">Creating the Object Model</span></span>](creating-the-object-model.md)
