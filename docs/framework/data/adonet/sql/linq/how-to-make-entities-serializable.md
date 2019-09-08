---
title: 'Instrukcje: Umożliwianie serializacji jednostek'
ms.date: 03/30/2017
ms.assetid: a6c5bf6e-064a-4f77-b74c-76b3a5dec309
ms.openlocfilehash: 40a0b4d5a49f88af1bedcbefdd117f6c000b791d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70793565"
---
# <a name="how-to-make-entities-serializable"></a><span data-ttu-id="213c7-102">Instrukcje: Umożliwianie serializacji jednostek</span><span class="sxs-lookup"><span data-stu-id="213c7-102">How to: Make Entities Serializable</span></span>
<span data-ttu-id="213c7-103">Jednostki można serializować podczas generowania kodu.</span><span class="sxs-lookup"><span data-stu-id="213c7-103">You can make entities serializable when you generate your code.</span></span> <span data-ttu-id="213c7-104">Klasy jednostek są dekoracyjne <xref:System.Runtime.Serialization.DataContractAttribute> i są kolumnami <xref:System.Runtime.Serialization.DataMemberAttribute> z atrybutem.</span><span class="sxs-lookup"><span data-stu-id="213c7-104">Entity classes are decorated with the <xref:System.Runtime.Serialization.DataContractAttribute> attribute, and columns with the <xref:System.Runtime.Serialization.DataMemberAttribute> attribute.</span></span>  
  
 <span data-ttu-id="213c7-105">Deweloperzy korzystający z programu Visual Studio mogą w tym celu używać Object Relational Designer.</span><span class="sxs-lookup"><span data-stu-id="213c7-105">Developers using Visual Studio can use the Object Relational Designer for this purpose.</span></span>  
  
 <span data-ttu-id="213c7-106">Jeśli używasz narzędzia wiersza polecenia SQLMetal, użyj opcji **/Serialization** z `unidirectional` argumentem.</span><span class="sxs-lookup"><span data-stu-id="213c7-106">If you are using the SQLMetal command-line tool, use the **/serialization** option with the `unidirectional` argument.</span></span> <span data-ttu-id="213c7-107">Aby uzyskać więcej informacji, zobacz [SQLMetal. exe (Narzędzie generowania kodu)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span><span class="sxs-lookup"><span data-stu-id="213c7-107">For more information, see [SqlMetal.exe (Code Generation Tool)](../../../../tools/sqlmetal-exe-code-generation-tool.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="213c7-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="213c7-108">Example</span></span>  
 <span data-ttu-id="213c7-109">Następujące wiersze poleceń SQLMetal tworzą pliki, które mają możliwe do serializacji jednostki.</span><span class="sxs-lookup"><span data-stu-id="213c7-109">The following SQLMetal command lines produce files that have serializable entities.</span></span>  
  
```  
sqlmetal /code:nwserializable.vb /language:vb "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
```  
sqlmetal /code:nwserializable.cs /language:csharp "c:\northwnd.mdf" /sprocs /functions /pluralize /serialization:unidirectional  
```  
  
## <a name="see-also"></a><span data-ttu-id="213c7-110">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="213c7-110">See also</span></span>

- [<span data-ttu-id="213c7-111">Serializacja</span><span class="sxs-lookup"><span data-stu-id="213c7-111">Serialization</span></span>](serialization.md)
- [<span data-ttu-id="213c7-112">Tworzenie modelu obiektu</span><span class="sxs-lookup"><span data-stu-id="213c7-112">Creating the Object Model</span></span>](creating-the-object-model.md)
