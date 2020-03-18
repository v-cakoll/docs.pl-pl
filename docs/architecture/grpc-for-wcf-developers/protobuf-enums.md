---
title: Wyliczenia Protobuf - gRPC dla programistów WCF
description: Dowiedz się, jak deklarować i używać wyliczeń w Protobuf.
ms.date: 09/09/2019
ms.openlocfilehash: 2177f568a671fa0e651625c6e025ac70c243feb5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79148078"
---
# <a name="protobuf-enumerations"></a><span data-ttu-id="4fafb-103">Wyliczenia Protobuf</span><span class="sxs-lookup"><span data-stu-id="4fafb-103">Protobuf enumerations</span></span>

<span data-ttu-id="4fafb-104">Protobuf obsługuje typy wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4fafb-104">Protobuf supports enumeration types.</span></span> <span data-ttu-id="4fafb-105">Ta obsługa była obsypana w poprzedniej sekcji, gdzie `Oneof` wyliczenie zostało użyte do określenia typu pola.</span><span class="sxs-lookup"><span data-stu-id="4fafb-105">You saw this support in the previous section, where an enum was used to determine the type of a `Oneof` field.</span></span> <span data-ttu-id="4fafb-106">Można zdefiniować własne typy wyliczenia i Protobuf skompiluje je do typów wyliczenia C#.</span><span class="sxs-lookup"><span data-stu-id="4fafb-106">You can define your own enumeration types, and Protobuf will compile them to C# enum types.</span></span>

<span data-ttu-id="4fafb-107">Ponieważ można użyć Protobuf z różnych języków, konwencje nazewnictwa dla wyliczenia różnią się od konwencji C#.</span><span class="sxs-lookup"><span data-stu-id="4fafb-107">Because you can use Protobuf with various languages, the naming conventions for enumerations are different from the C# conventions.</span></span> <span data-ttu-id="4fafb-108">Jednak generator kodu konwertuje nazwy na tradycyjny przypadek C#.</span><span class="sxs-lookup"><span data-stu-id="4fafb-108">However, the code generator converts the names to the traditional C# case.</span></span> <span data-ttu-id="4fafb-109">Jeśli odpowiednik pascala przypadku nazwy pola zaczyna się od nazwy wyliczenia, a następnie jest usuwany.</span><span class="sxs-lookup"><span data-stu-id="4fafb-109">If the Pascal-case equivalent of the field name starts with the enumeration name, then it's removed.</span></span>

<span data-ttu-id="4fafb-110">Na przykład w poniższym wyliczeniu Protobuf pola `ACCOUNT_STATUS`są poprzedzone .</span><span class="sxs-lookup"><span data-stu-id="4fafb-110">For example, in the following Protobuf enumeration, the fields are prefixed with `ACCOUNT_STATUS`.</span></span> <span data-ttu-id="4fafb-111">Ten prefiks jest odpowiednikiem nazwy wyliczenia litery Pascal. `AccountStatus`</span><span class="sxs-lookup"><span data-stu-id="4fafb-111">This prefix is equivalent to the Pascal-case enum name, `AccountStatus`.</span></span>

```protobuf
enum AccountStatus {
  ACCOUNT_STATUS_UNKNOWN = 0;
  ACCOUNT_STATUS_PENDING = 1;
  ACCOUNT_STATUS_ACTIVE = 2;
  ACCOUNT_STATUS_SUSPENDED = 3;
  ACCOUNT_STATUS_CLOSED = 4;
}
```

<span data-ttu-id="4fafb-112">Generator tworzy wyliczenie Języka C# równoważne następującemu kodzie:</span><span class="sxs-lookup"><span data-stu-id="4fafb-112">The generator creates a C# enum equivalent to the following code:</span></span>

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

<span data-ttu-id="4fafb-113">Definicje wyliczenia protobuf *musi* mieć stałą zerową jako pierwsze pole.</span><span class="sxs-lookup"><span data-stu-id="4fafb-113">Protobuf enumeration definitions *must* have a zero constant as their first field.</span></span> <span data-ttu-id="4fafb-114">Podobnie jak w języku C#, można zadeklarować wiele pól o tej samej wartości.</span><span class="sxs-lookup"><span data-stu-id="4fafb-114">As in C#, you can declare multiple fields with the same value.</span></span> <span data-ttu-id="4fafb-115">Należy jednak jawnie włączyć tę `allow_alias` opcję, korzystając z opcji w wyliczeniu:</span><span class="sxs-lookup"><span data-stu-id="4fafb-115">But you must explicitly enable this option by using the `allow_alias` option in the enum:</span></span>

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

<span data-ttu-id="4fafb-116">Można zadeklarować wyliczenia na najwyższym `.proto` poziomie w pliku lub zagnieżdżone w definicji wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4fafb-116">You can declare enumerations at the top level in a `.proto` file, or nested within a message definition.</span></span> <span data-ttu-id="4fafb-117">Zagnieżdżone wyliczenia — takie jak `.Types` zagnieżdżone wiadomości — będą deklarowane w klasie statycznej w wygenerowanej klasie wiadomości.</span><span class="sxs-lookup"><span data-stu-id="4fafb-117">Nested enumerations—like nested messages—will be declared within the `.Types` static class in the generated message class.</span></span>

<span data-ttu-id="4fafb-118">Nie ma możliwości zastosowania atrybutu [[Flags]](xref:System.FlagsAttribute) do wyliczenia wygenerowanego przez Protobuf, a Protobuf nie rozumie kombinacji wyliczenia bitowego.</span><span class="sxs-lookup"><span data-stu-id="4fafb-118">There's no way to apply the [[Flags]](xref:System.FlagsAttribute) attribute to a Protobuf-generated enum, and Protobuf doesn't understand bitwise enum combinations.</span></span> <span data-ttu-id="4fafb-119">Spójrz na poniższy przykład:</span><span class="sxs-lookup"><span data-stu-id="4fafb-119">Look at the following example:</span></span>

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

<span data-ttu-id="4fafb-120">Jeśli ustawisz `product.AvailableIn` `Region.NorthAmerica | Region.SouthAmerica`, jest serializowany jako wartość `3`całkowita .</span><span class="sxs-lookup"><span data-stu-id="4fafb-120">If you set `product.AvailableIn` to `Region.NorthAmerica | Region.SouthAmerica`, it's serialized as the integer value `3`.</span></span> <span data-ttu-id="4fafb-121">Gdy klient lub serwer próbuje deserializować wartość, nie znajdzie dopasowania w definicji wyliczenia dla `3`.</span><span class="sxs-lookup"><span data-stu-id="4fafb-121">When a client or server tries to deserialize the value, it won't find a match in the enum definition for `3`.</span></span> <span data-ttu-id="4fafb-122">Wynik będzie `Region.None`.</span><span class="sxs-lookup"><span data-stu-id="4fafb-122">The result will be `Region.None`.</span></span>

<span data-ttu-id="4fafb-123">Najlepszym sposobem pracy z wieloma wartościami wyliczenia w `repeated` Protobuf jest użycie pola typu wyliczenia.</span><span class="sxs-lookup"><span data-stu-id="4fafb-123">The best way to work with multiple enum values in Protobuf is to use a `repeated` field of the enum type.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4fafb-124">[Poprzedni](protobuf-any-oneof.md)
>[następny](protobuf-maps.md)</span><span class="sxs-lookup"><span data-stu-id="4fafb-124">[Previous](protobuf-any-oneof.md)
[Next](protobuf-maps.md)</span></span>
