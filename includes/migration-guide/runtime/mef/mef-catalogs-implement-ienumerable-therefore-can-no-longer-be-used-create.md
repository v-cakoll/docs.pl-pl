---
ms.openlocfilehash: 598df2121b480d411dac9c5571772a4a8d22b5ff
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85620338"
---
### <a name="mef-catalogs-implement-ienumerable-and-therefore-can-no-longer-be-used-to-create-a-serializer"></a><span data-ttu-id="4f7fc-101">Wykazy MEF implementują interfejs IEnumerable i w związku z tym nie mogą być już używane do tworzenia serializatora</span><span class="sxs-lookup"><span data-stu-id="4f7fc-101">MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer</span></span>

#### <a name="details"></a><span data-ttu-id="4f7fc-102">Szczegóły</span><span class="sxs-lookup"><span data-stu-id="4f7fc-102">Details</span></span>

<span data-ttu-id="4f7fc-103">Począwszy od .NET Framework 4,5, wykazy MEF implementują interfejs IEnumerable i w związku z tym nie można już używać do tworzenia serializatora ( <xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> obiektu).</span><span class="sxs-lookup"><span data-stu-id="4f7fc-103">Starting with the .NET Framework 4.5, MEF catalogs implement IEnumerable and therefore can no longer be used to create a serializer (<xref:System.Xml.Serialization.XmlSerializer?displayProperty=fullName> object).</span></span> <span data-ttu-id="4f7fc-104">Próba serializowania katalogu MEF powoduje zgłoszenie wyjątku.</span><span class="sxs-lookup"><span data-stu-id="4f7fc-104">Trying to serialize a MEF catalog throws an exception.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="4f7fc-105">Sugestia</span><span class="sxs-lookup"><span data-stu-id="4f7fc-105">Suggestion</span></span>

<span data-ttu-id="4f7fc-106">Nie można już używać MEF do tworzenia serializatora</span><span class="sxs-lookup"><span data-stu-id="4f7fc-106">Can no longer use MEF to create a serializer</span></span>

| <span data-ttu-id="4f7fc-107">Nazwa</span><span class="sxs-lookup"><span data-stu-id="4f7fc-107">Name</span></span>    | <span data-ttu-id="4f7fc-108">Wartość</span><span class="sxs-lookup"><span data-stu-id="4f7fc-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="4f7fc-109">Zakres</span><span class="sxs-lookup"><span data-stu-id="4f7fc-109">Scope</span></span>   |<span data-ttu-id="4f7fc-110">Duży</span><span class="sxs-lookup"><span data-stu-id="4f7fc-110">Major</span></span>|
|<span data-ttu-id="4f7fc-111">Wersja</span><span class="sxs-lookup"><span data-stu-id="4f7fc-111">Version</span></span>|<span data-ttu-id="4f7fc-112">4.5</span><span class="sxs-lookup"><span data-stu-id="4f7fc-112">4.5</span></span>|
|<span data-ttu-id="4f7fc-113">Typ</span><span class="sxs-lookup"><span data-stu-id="4f7fc-113">Type</span></span>|<span data-ttu-id="4f7fc-114">Środowisko uruchomieniowe</span><span class="sxs-lookup"><span data-stu-id="4f7fc-114">Runtime</span></span>|
