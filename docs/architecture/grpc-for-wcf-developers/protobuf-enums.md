---
title: Wyliczenia protobuf — gRPC dla deweloperów WCF
description: Dowiedz się, jak deklarować wyliczenia i korzystać z nich w protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 01cf4a4e5e0eda1e7ddff2a6780119fcb3120dad
ms.sourcegitcommit: 771c554c84ba38cbd4ac0578324ec4cfc979cf2e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/21/2020
ms.locfileid: "77543147"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="06aa7-103">Wyliczenia Protobuf</span><span class="sxs-lookup"><span data-stu-id="06aa7-103">Protobuf enumerations</span></span>

<span data-ttu-id="06aa7-104">Protobuf obsługuje typy wyliczeniowe.</span><span class="sxs-lookup"><span data-stu-id="06aa7-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="06aa7-105">Ta obsługa jest obsługiwana w poprzedniej sekcji, gdzie Wyliczenie zostało użyte do określenia typu pola `Oneof`.</span><span class="sxs-lookup"><span data-stu-id="06aa7-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="06aa7-106">Można zdefiniować własne typy wyliczeniowe, a protobuf będzie kompilować je do C# typów wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="06aa7-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span> 

<span data-ttu-id="06aa7-107">Ponieważ można używać protobuf z różnymi językami, konwencje nazewnictwa dla wyliczeń różnią C# się od konwencji.</span><span class="sxs-lookup"><span data-stu-id="06aa7-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="06aa7-108">Jednak generator kodu konwertuje nazwy do tradycyjnego C# przypadku.</span><span class="sxs-lookup"><span data-stu-id="06aa7-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="06aa7-109">Jeśli odpowiednik w przypadku języka Pascala nazwy pola rozpoczyna się od nazwy wyliczenia, zostanie usunięty.</span><span class="sxs-lookup"><span data-stu-id="06aa7-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="06aa7-110">Na przykład w poniższym wyliczeniu protobuf pola są poprzedzone prefiksem `ACCOUNT_STATUS`.</span><span class="sxs-lookup"><span data-stu-id="06aa7-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="06aa7-111">Ten prefiks jest równoważny z nazwą wyliczenia przypadku w języku Pascal, `AccountStatus`.</span><span class="sxs-lookup"><span data-stu-id="06aa7-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="06aa7-112">Generator tworzy C# odpowiednik w następującym kodzie:</span><span class="sxs-lookup"><span data-stu-id="06aa7-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="06aa7-113">Definicje wyliczenia protobuf *muszą* mieć stałą zero jako swoje pierwsze pole.</span><span class="sxs-lookup"><span data-stu-id="06aa7-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="06aa7-114">Podobnie jak C#w programie, można zadeklarować wiele pól o tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="06aa7-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="06aa7-115">Należy jednak jawnie włączyć tę opcję przy użyciu opcji `allow_alias` w wyliczeniu:</span><span class="sxs-lookup"><span data-stu-id="06aa7-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="06aa7-116">Wyliczenia można zadeklarować na najwyższym poziomie w pliku `.proto` lub zagnieżdżać w ramach definicji komunikatu.</span><span class="sxs-lookup"><span data-stu-id="06aa7-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="06aa7-117">Wyliczenia zagnieżdżone — takie jak komunikaty zagnieżdżone — zostaną zadeklarowane w obrębie klasy statycznej `.Types` w wygenerowanej klasie komunikatów.</span><span class="sxs-lookup"><span data-stu-id="06aa7-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="06aa7-118">Nie ma sposobu zastosowania atrybutu [[flags]](xref:System.FlagsAttribute) do wyliczenia wygenerowanego przez protobuf, a protobuf nie rozpoznaje bitowych kombinacji wyliczeniowych.</span><span class="sxs-lookup"><span data-stu-id="06aa7-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="06aa7-119">Zapoznaj się z poniższym przykładem:</span><span class="sxs-lookup"><span data-stu-id="06aa7-119">Look at the following example:</span></span>

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

<span data-ttu-id="06aa7-120">Jeśli ustawisz `product.AvailableIn` na `Region.NorthAmerica | Region.SouthAmerica`, zostanie ona zserializowana jako wartość całkowita `3`.</span><span class="sxs-lookup"><span data-stu-id="06aa7-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="06aa7-121">Gdy klient lub serwer próbuje zdeserializować wartości, nie znajdzie dopasowania w definicji wyliczenia dla `3`.</span><span class="sxs-lookup"><span data-stu-id="06aa7-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="06aa7-122">Wynik zostanie `Region.None`.</span><span class="sxs-lookup"><span data-stu-id="06aa7-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="06aa7-123">Najlepszym sposobem pracy z wieloma wartościami wyliczenia w protobuf jest użycie pola `repeated` typu wyliczeniowego.</span><span class="sxs-lookup"><span data-stu-id="06aa7-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="06aa7-124">[Poprzednie](protobuf-any-oneof.md)
>[dalej](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="06aa7-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
