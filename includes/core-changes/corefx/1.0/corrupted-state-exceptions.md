---
ms.openlocfilehash: 394f2daebad7b6af94bee4d7876796e87fe8ab19
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135632"
---
### <a name="handling-corrupted-state-exceptions-is-not-supported"></a><span data-ttu-id="5ee43-101">Obsługa wyjątków uszkodzonych stanów nie jest obsługiwana</span><span class="sxs-lookup"><span data-stu-id="5ee43-101">Handling corrupted state exceptions is not supported</span></span>

<span data-ttu-id="5ee43-102">Obsługa wyjątków uszkodzonego stanu procesu w programie .NET Core nie jest obsługiwana.</span><span class="sxs-lookup"><span data-stu-id="5ee43-102">Handling corrupted-process-state exceptions in .NET Core is not supported.</span></span>

#### <a name="change-description"></a><span data-ttu-id="5ee43-103">Zmień opis</span><span class="sxs-lookup"><span data-stu-id="5ee43-103">Change description</span></span>

<span data-ttu-id="5ee43-104">Wcześniej wyjątki z uszkodzonym stanem procesu mogą być przechwytywane i obsługiwane przez program obsługi wyjątków kodu zarządzanego, na przykład przy użyciu instrukcji [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) w języku C#.</span><span class="sxs-lookup"><span data-stu-id="5ee43-104">Previously, corrupted-process-state exceptions could be caught and handled by managed code exception handlers, for example, by using a [try-catch](../../../../docs/csharp/language-reference/keywords/try-catch.md) statement in C#.</span></span>

<span data-ttu-id="5ee43-105">Począwszy od platformy .NET Core 1,0, wyjątki stanu uszkodzonego procesu nie mogą być obsługiwane przez kod zarządzany.</span><span class="sxs-lookup"><span data-stu-id="5ee43-105">Starting in .NET Core 1.0, corrupted-process-state exceptions cannot be handled by managed code.</span></span> <span data-ttu-id="5ee43-106">Środowisko uruchomieniowe języka wspólnego nie dostarcza wyjątków o uszkodzonym stanie do kodu zarządzanego.</span><span class="sxs-lookup"><span data-stu-id="5ee43-106">The common language runtime doesn't deliver corrupted-process-state exceptions to managed code.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="5ee43-107">Wprowadzona wersja</span><span class="sxs-lookup"><span data-stu-id="5ee43-107">Version introduced</span></span>

<span data-ttu-id="5ee43-108">1.0</span><span class="sxs-lookup"><span data-stu-id="5ee43-108">1.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="5ee43-109">Zalecana akcja</span><span class="sxs-lookup"><span data-stu-id="5ee43-109">Recommended action</span></span>

<span data-ttu-id="5ee43-110">Należy unikać konieczności obsługi wyjątków uszkodzonego stanu przez odnoszące się do nich sytuacje.</span><span class="sxs-lookup"><span data-stu-id="5ee43-110">Avoid the need to handle corrupted-process-state exceptions by addressing the situations that lead to them instead.</span></span> <span data-ttu-id="5ee43-111">Jeśli jest absolutnie niezbędne do obsługi wyjątków uszkodzonego stanu procesu, należy napisać procedurę obsługi wyjątków w kodzie C lub C++.</span><span class="sxs-lookup"><span data-stu-id="5ee43-111">If it's absolutely necessary to handle corrupted-process-state exceptions, write the exception handler in C or C++ code.</span></span>

#### <a name="category"></a><span data-ttu-id="5ee43-112">Kategoria</span><span class="sxs-lookup"><span data-stu-id="5ee43-112">Category</span></span>

<span data-ttu-id="5ee43-113">Podstawowe biblioteki platformy .NET</span><span class="sxs-lookup"><span data-stu-id="5ee43-113">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="5ee43-114">Dotyczy interfejsów API</span><span class="sxs-lookup"><span data-stu-id="5ee43-114">Affected APIs</span></span>

- <xref:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute?displayProperty=fullName>
- [<span data-ttu-id="5ee43-115">legacyCorruptedStateExceptionsPolicy, element</span><span class="sxs-lookup"><span data-stu-id="5ee43-115">legacyCorruptedStateExceptionsPolicy element</span></span>](~/docs/framework/configure-apps/file-schema/runtime/legacycorruptedstateexceptionspolicy-element.md)

<!--

#### Affected APIs

- `T:System.Runtime.ExceptionServices.HandleProcessCorruptedStateExceptionsAttribute`

-->
