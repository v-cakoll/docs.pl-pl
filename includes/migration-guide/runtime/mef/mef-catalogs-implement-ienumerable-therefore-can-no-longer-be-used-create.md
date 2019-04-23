---
ms.openlocfilehash: 4cc91e7c6054fdb8e96cecf7120df5b9f25de56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59804773"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="193df-101">Katalogi MEF implementować interfejs IEnumerable i w związku z tym może już służyć do tworzenia serializatora</span><span class="sxs-lookup"><span data-stu-id="193df-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

|   |   |
|---|---|
|<span data-ttu-id="193df-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="193df-102">Details</span></span>|<span data-ttu-id="193df-103">Począwszy od programu .NET Framework 4.5, implementować interfejs IEnumerable katalogach MEF i dlatego nie będzie można utworzyć programu szeregującego (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> obiektu).</span><span class="sxs-lookup"><span data-stu-id="193df-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=name> object).</span></span> <span data-ttu-id="193df-104">Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="193df-104">Trying to serialize a MEF catalog throws an exception.</span></span>|
|<span data-ttu-id="193df-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="193df-105">Suggestion</span></span>|<span data-ttu-id="193df-106">Nie można korzystać MEF do tworzenia serializatora</span><span class="sxs-lookup"><span data-stu-id="193df-106">Can no longer use MEF to create a serializer</span></span>|
|<span data-ttu-id="193df-107">Zakres</span><span class="sxs-lookup"><span data-stu-id="193df-107">Scope</span></span>|<span data-ttu-id="193df-108">Duży</span><span class="sxs-lookup"><span data-stu-id="193df-108">Major</span></span>|
|<span data-ttu-id="193df-109">Wersja</span><span class="sxs-lookup"><span data-stu-id="193df-109">Version</span></span>|<span data-ttu-id="193df-110">4.5</span><span class="sxs-lookup"><span data-stu-id="193df-110">4.5</span></span>|
|<span data-ttu-id="193df-111">Typ</span><span class="sxs-lookup"><span data-stu-id="193df-111">Type</span></span>|<span data-ttu-id="193df-112">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="193df-112">Runtime</span></span>|
