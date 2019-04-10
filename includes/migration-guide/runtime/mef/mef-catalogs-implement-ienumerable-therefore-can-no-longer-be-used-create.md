---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59235576"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="255f7-101">Katalogi MEF implementować interfejs IEnumerable i w związku z tym może już służyć do tworzenia serializatora</span><span class="sxs-lookup"><span data-stu-id="255f7-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

|   |   |
|---|---|
|<span data-ttu-id="255f7-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="255f7-102">Details</span></span>|<span data-ttu-id="255f7-103">Począwszy od programu .NET Framework 4.5, implementować interfejs IEnumerable katalogach MEF i dlatego nie będzie można utworzyć programu szeregującego (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> obiektu).</span><span class="sxs-lookup"><span data-stu-id="255f7-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> object).</span></span> <span data-ttu-id="255f7-104">Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="255f7-104">Trying to serialize a MEF catalog throws an exception.</span></span>|
|<span data-ttu-id="255f7-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="255f7-105">Suggestion</span></span>|<span data-ttu-id="255f7-106">Nie można korzystać MEF do tworzenia serializatora</span><span class="sxs-lookup"><span data-stu-id="255f7-106">Can no longer use MEF to create a serializer</span></span>|
|<span data-ttu-id="255f7-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="255f7-107">Scope</span></span>|<span data-ttu-id="255f7-108">Duży</span><span class="sxs-lookup"><span data-stu-id="255f7-108">Major</span></span>|
|<span data-ttu-id="255f7-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="255f7-109">Version</span></span>|<span data-ttu-id="255f7-110">4.5</span><span class="sxs-lookup"><span data-stu-id="255f7-110">4.5</span></span>|
|<span data-ttu-id="255f7-111">Typ</span><span class="sxs-lookup"><span data-stu-id="255f7-111">Type</span></span>|<span data-ttu-id="255f7-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="255f7-112">Runtime</span></span>|
