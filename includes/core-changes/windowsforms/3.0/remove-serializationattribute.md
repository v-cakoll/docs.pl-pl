---
ms.openlocfilehash: d48ced9d0201a33f9149aba155ddd3d8bc04c93f
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74643957"
---
### <a name="serializableattribute-removed-from-some-windows-forms-types"></a><span data-ttu-id="8d3e3-101">SerializableAttribute usunięte z niektórych typów formularzy systemu Windows</span><span class="sxs-lookup"><span data-stu-id="8d3e3-101">SerializableAttribute removed from some Windows Forms types</span></span>

<span data-ttu-id="8d3e3-102">Został <xref:System.SerializableAttribute> usunięty z niektórych klas formularzy systemu Windows, które nie mają znanych scenariuszy serializacji binarnej.</span><span class="sxs-lookup"><span data-stu-id="8d3e3-102">The <xref:System.SerializableAttribute> has been removed from some Windows Forms classes that have no known binary serialization scenarios.</span></span>

#### <a name="change-description"></a><span data-ttu-id="8d3e3-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="8d3e3-103">Change description</span></span>

<span data-ttu-id="8d3e3-104">Następujące typy są ozdobione <xref:System.SerializableAttribute> w .NET Framework, ale atrybut został usunięty w .NET Core:</span><span class="sxs-lookup"><span data-stu-id="8d3e3-104">The following types are decorated with the <xref:System.SerializableAttribute> in .NET Framework, but the attribute has been removed in .NET Core:</span></span>

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

<span data-ttu-id="8d3e3-105">Historycznie ten mechanizm serializacji miał poważne problemy z konserwacją i bezpieczeństwem.</span><span class="sxs-lookup"><span data-stu-id="8d3e3-105">Historically, this serialization mechanism has had serious maintenance and security concerns.</span></span> <span data-ttu-id="8d3e3-106">Utrzymywanie `SerializableAttribute` na typy oznacza, że te typy muszą być testowane pod kątem zmian serializacji wersji do wersji i potencjalnie framework-to-framework zmiany serializacji.</span><span class="sxs-lookup"><span data-stu-id="8d3e3-106">Maintaining `SerializableAttribute` on types means those types must be tested for version-to-version serialization changes and potentially framework-to-framework serialization changes.</span></span> <span data-ttu-id="8d3e3-107">To sprawia, że trudniej rozwijać te typy i może być kosztowne w utrzymaniu.</span><span class="sxs-lookup"><span data-stu-id="8d3e3-107">This makes it harder to evolve those types and can be costly to maintain.</span></span> <span data-ttu-id="8d3e3-108">Te typy nie mają znanych scenariuszy serializacji binarnych, co minimalizuje wpływ usuwania atrybutu.</span><span class="sxs-lookup"><span data-stu-id="8d3e3-108">These types have no known binary serialization scenarios, which minimizes the impact of removing the attribute.</span></span>

<span data-ttu-id="8d3e3-109">Aby uzyskać więcej informacji, zobacz [Serializacja binarna](~/docs/standard/serialization/binary-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="8d3e3-109">For more information, see [Binary serialization](~/docs/standard/serialization/binary-serialization.md).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="8d3e3-110">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="8d3e3-110">Version introduced</span></span>

<span data-ttu-id="8d3e3-111">3.0 Podgląd 9</span><span class="sxs-lookup"><span data-stu-id="8d3e3-111">3.0 Preview 9</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="8d3e3-112">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="8d3e3-112">Recommended action</span></span>

<span data-ttu-id="8d3e3-113">Zaktualizuj dowolny kod, który może zależeć od tych typów są oznaczone jako serializacji.</span><span class="sxs-lookup"><span data-stu-id="8d3e3-113">Update any code that may depend on these types being marked as serializable.</span></span>

#### <a name="category"></a><span data-ttu-id="8d3e3-114">Kategoria</span><span class="sxs-lookup"><span data-stu-id="8d3e3-114">Category</span></span>

<span data-ttu-id="8d3e3-115">Windows Forms</span><span class="sxs-lookup"><span data-stu-id="8d3e3-115">Windows Forms</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="8d3e3-116">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="8d3e3-116">Affected APIs</span></span>

- <span data-ttu-id="8d3e3-117">Brak</span><span class="sxs-lookup"><span data-stu-id="8d3e3-117">None</span></span>

<!--

### Affected APIs

- Not detectable via API analysis

-->
