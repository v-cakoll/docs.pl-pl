---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/24/2019
ms.locfileid: "71217046"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="d1305-101">SerializableAttribute usunięte z niektórych typów Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1305-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="d1305-102">Program <xref:System.SerializableAttribute> został usunięty z niektórych klas Windows Forms, które nie mają znanych scenariuszy serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="d1305-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="d1305-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="d1305-103">Change description</span></span>

<span data-ttu-id="d1305-104">Następujące typy są dekoracyjne <xref:System.SerializableAttribute> w .NET Framework, ale atrybut został usunięty z platformy .NET Core:</span><span class="sxs-lookup"><span data-stu-id="d1305-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

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

<span data-ttu-id="d1305-105">W przeszłości ten mechanizm serializacji miał poważne problemy związane z konserwacją i bezpieczeństwem.</span><span class="sxs-lookup"><span data-stu-id="d1305-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="d1305-106">Utrzymywanie `SerializableAttribute` na typach oznacza, że te typy muszą być testowane pod kątem zmian serializacji z wersji do wersji oraz ewentualnych zmian serializacji między platformami.</span><span class="sxs-lookup"><span data-stu-id="d1305-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="d1305-107">Dzięki temu trudniej jest rozwijać te typy i mogą być kosztowne do utrzymania.</span><span class="sxs-lookup"><span data-stu-id="d1305-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="d1305-108">Te typy nie mają znanych scenariuszy serializacji binarnej, co minimalizuje wpływ usuwania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="d1305-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="d1305-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="d1305-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="d1305-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="d1305-110">Version introduced</span></span>

<span data-ttu-id="d1305-111">3,0 wersja zapoznawcza 9</span><span class="sxs-lookup"><span data-stu-id="d1305-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="d1305-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="d1305-112">Recommended action</span></span>

<span data-ttu-id="d1305-113">Zaktualizuj każdy kod, który może zależeć od tych typów jako możliwy do serializacji.</span><span class="sxs-lookup"><span data-stu-id="d1305-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="d1305-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="d1305-114">Category</span></span>

<span data-ttu-id="d1305-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d1305-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="d1305-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="d1305-116">Affected APIs</span></span>

- <span data-ttu-id="d1305-117">Brak</span><span class="sxs-lookup"><span data-stu-id="d1305-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
