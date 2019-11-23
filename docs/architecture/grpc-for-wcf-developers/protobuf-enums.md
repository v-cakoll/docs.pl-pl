---
title: Wyliczenia protobuf — gRPC dla deweloperów WCF
description: Dowiedz się, jak deklarować wyliczenia i korzystać z nich w protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 4ea4d03bede2a9ebfd1f2c3ee56f299e918800e9
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971574"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="8f044-103">Wyliczenia Protobuf</span><span class="sxs-lookup"><span data-stu-id="8f044-103">Protobuf enumerations</span></span>

<span data-ttu-id="8f044-104">Protobuf obsługuje typy wyliczeniowe, jak pokazano w poprzedniej sekcji, w której Wyliczenie zostało użyte do określenia typu pola `oneof`.</span><span class="sxs-lookup"><span data-stu-id="8f044-104">Protobuf supports enumeration types, as seen in the previous section where an enum was used to determine the type of a `oneof` field.</span></span> <span data-ttu-id="8f044-105">Można zdefiniować własne typy wyliczeniowe, a protobuf będzie kompilować je C# do typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="8f044-105">You can define your own enumeration types and Protobuf will compile them to C# enum types.</span></span> <span data-ttu-id="8f044-106">Ponieważ protobuf można używać w różnych językach, konwencje nazewnictwa dla wyliczeń różnią się C# od konwencji.</span><span class="sxs-lookup"><span data-stu-id="8f044-106">Since Protobuf can be used with different languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="8f044-107">Jednak generator kodu jest sprytne i konwertuje nazwy do tradycyjnego C# przypadku.</span><span class="sxs-lookup"><span data-stu-id="8f044-107">However, the code generator is clever and converts the names to the traditional C# case.</span></span> <span data-ttu-id="8f044-108">Jeśli odpowiednik w przypadku języka Pascala nazwy pola rozpoczyna się od nazwy wyliczenia, zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="8f044-108">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="8f044-109">Na przykład w tym wyliczeniu protobuf pola są poprzedzone `ACCOUNT_STATUS`, co jest równoznaczne z nazwą wyliczenia przypadku w języku Pascal: `AccountStatus`.</span><span class="sxs-lookup"><span data-stu-id="8f044-109">For example, in this Protobuf enumeration the fields are prefixed with `ACCOUNT_STATUS`, which is equivalent to the Pascal case enum name: `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="8f044-110">W ten sposób Generator tworzy C# równoważność następującego kodu:</span><span class="sxs-lookup"><span data-stu-id="8f044-110">So, the generator creates a C# enum equivalent to the following code:</span></span>

```csharp
public enum AccountStatus
{
    Unknown = 0,
    Pending = 1,
    Active = 2,
    Suspended = 3,
    Closed = 4
}
```

<span data-ttu-id="8f044-111">Definicje wyliczenia protobuf **muszą** mieć stałą zero jako swoje pierwsze pole.</span><span class="sxs-lookup"><span data-stu-id="8f044-111">Protobuf enumeration definitions **must** have a zero constant as their first field.</span></span> <span data-ttu-id="8f044-112">Podobnie jak C#w programie, można zadeklarować wiele pól o tej samej wartości, ale należy jawnie włączyć tę opcję przy użyciu opcji `allow_alias` w wyliczeniu:</span><span class="sxs-lookup"><span data-stu-id="8f044-112">As in C#, you can declare multiple fields with the same value, but you must explicitly enable this option using the `allow_alias` option in the enum:</span></span>

```protobuf
enum AccountStatus {
  option allow_alias = true;
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
  ACCOUNT_STATUS_CANCELLED = 4;
}
```

<span data-ttu-id="8f044-113">Wyliczenia można zadeklarować na najwyższym poziomie w pliku `.proto` lub zagnieżdżać w ramach definicji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="8f044-113">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="8f044-114">Wyliczenia zagnieżdżone — takie jak komunikaty zagnieżdżone — zostaną zadeklarowane w obrębie klasy statycznej `.Types` w wygenerowanej klasie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="8f044-114">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="8f044-115">Nie ma sposobu zastosowania atrybutu [[flags]](xref:System.FlagsAttribute) do wyliczenia wygenerowanego przez protobuf, a protobuf nie rozpoznaje bitowych kombinacji wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="8f044-115">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="8f044-116">Zapoznaj się z poniższym przykładem:</span><span class="sxs-lookup"><span data-stu-id="8f044-116">Take a look at the following example:</span></span>

```protobuf
enum Region {
  REGION_NONE = 0;
  REGION_NORTH_AMERICA = 1;
  REGION_SOUTH_AMERICA = 2;
  REGION_EMEA = 4;
  REGION_APAC = 8;
}

message Product {
  Region available_in = 1;
}
```

<span data-ttu-id="8f044-117">Jeśli ustawisz `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, zostanie ona zserializowana jako wartość całkowita `3`.</span><span class="sxs-lookup"><span data-stu-id="8f044-117">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="8f044-118">Gdy klient lub serwer próbuje zdeserializować wartości, nie znajdzie dopasowania w definicji wyliczenia dla `3`, a wynik zostanie `Region.None`.</span><span class="sxs-lookup"><span data-stu-id="8f044-118">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3` and the result will be `Region.None`.</span></span>

<span data-ttu-id="8f044-119">Najlepszym sposobem pracy z wieloma wartościami wyliczenia w protobuf jest użycie pola `repeated` typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="8f044-119">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8f044-120">[Poprzedni](protobuf-any-oneof.md)
>[Następny](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="8f044-120">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
