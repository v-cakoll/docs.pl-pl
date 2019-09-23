---
ms.openlocfilehash: e9d76d5907e7d700fc57117ccb43f8c430c615b0
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/23/2019
ms.locfileid: "71181834"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="546ed-101">SerializableAttribute usunięte z niektórych typów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="546ed-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="546ed-102">Program <xref:System.SerializableAttribute> został usunięty z niektórych klas Windows Forms, które nie mają znanych scenariuszy serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="546ed-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="546ed-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="546ed-103">Change description</span></span>

<span data-ttu-id="546ed-104">Następujące typy są dekoracyjne <xref:System.SerializableAttribute> w .NET Framework, ale atrybut został usunięty z platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="546ed-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

- `System.InvariantComparer`
- <xref:System.ComponentModel.Design.ExceptionCollection?displayProperty=nameWithType>
- <xref:System.ComponentModel.Design.Serialization.CodeDomSerializerException?displayProperty=nameWithType>
- `System.ComponentModel.Design.Serialization.CodeDomComponentSerializationService.CodeDomSerializationStore`
- <xref:System.Drawing.Design.ToolboxItem?displayProperty=nameWithType>
- `System.Resources.ResXNullRef`
- `System.Resources.ResXDataNode`
- `System.Resources.ResXFileRef`
- <xref:System.Windows.Forms.Cursor?displayProperty=nameWithType>
- `System.Windows.Forms.NativeMethods.MSOCRINFOSTRUCT`
- `System.Windows.Forms.NativeMethods.MSG`

<span data-ttu-id="546ed-105">W przeszłości ten mechanizm serializacji miał poważne problemy związane z konserwacją i bezpieczeństwem.</span><span class="sxs-lookup"><span data-stu-id="546ed-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="546ed-106">Utrzymywanie `SerializableAttribute` na typach oznacza, że te typy muszą być testowane pod kątem zmian serializacji z wersji do wersji oraz ewentualnych zmian serializacji między platformami.</span><span class="sxs-lookup"><span data-stu-id="546ed-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="546ed-107">Dzięki temu trudniej jest rozwijać te typy i mogą być kosztowne do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="546ed-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="546ed-108">Te typy nie mają znanych scenariuszy serializacji binarnej, co minimalizuje wpływ usuwania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="546ed-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="546ed-109">Aby uzyskać więcej informacji, zobacz <https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>.</span><span class="sxs-lookup"><span data-stu-id="546ed-109">For more information, see <https://docs.microsoft.com/en-us/dotnet/standard/serialization/binary-serialization>.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="546ed-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="546ed-110">Version introduced</span></span>

<span data-ttu-id="546ed-111">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="546ed-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="546ed-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="546ed-112">Recommended action</span></span>

<span data-ttu-id="546ed-113">Zaktualizuj każdy kod, który może zależeć od tych typów jako możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="546ed-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="546ed-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="546ed-114">Category</span></span>

<span data-ttu-id="546ed-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="546ed-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="546ed-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="546ed-116">Affected APIs</span></span>

- <span data-ttu-id="546ed-117">Brak</span><span class="sxs-lookup"><span data-stu-id="546ed-117">None</span></span>

<!-- 

### Affected APIs

- Not detectable via API analysis

-->