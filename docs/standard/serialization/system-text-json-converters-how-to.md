---
title: Jak pisać konwertery niestandardowe na potrzeby serializacji JSON — .NET
ms.date: 01/10/2020
no-loc:
- System.Text.Json
- Newtonsoft.Json
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 310967f39c3aa7a46d79087bcbf0cb016f7d7284
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159575"
---
# <a name="how-to-write-custom-converters-for-json-serialization-marshalling-in-net"></a><span data-ttu-id="fe326-102">Jak pisać konwertery niestandardowe na potrzeby serializacji JSON (kierowanie) w programie .NET</span><span class="sxs-lookup"><span data-stu-id="fe326-102">How to write custom converters for JSON serialization (marshalling) in .NET</span></span>

<span data-ttu-id="fe326-103">W tym artykule pokazano, jak utworzyć niestandardowe konwertery dla klas serializacji JSON, które są dostępne w przestrzeni nazw <xref:[!OP.NO-LOC(System.Text.Json)]>.</span><span class="sxs-lookup"><span data-stu-id="fe326-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:[!OP.NO-LOC(System.Text.Json)]> namespace.</span></span> <span data-ttu-id="fe326-104">Aby zapoznać się z wprowadzeniem do `[!OP.NO-LOC(System.Text.Json)]`, zobacz [jak serializować i deserializować kod JSON w programie .NET](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="fe326-104">For an introduction to `[!OP.NO-LOC(System.Text.Json)]`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="fe326-105">*Konwerter* jest klasą, która konwertuje obiekt lub wartość do i z formatu JSON.</span><span class="sxs-lookup"><span data-stu-id="fe326-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="fe326-106">Przestrzeń nazw `[!OP.NO-LOC(System.Text.Json)]` zawiera wbudowane konwertery dla większości typów pierwotnych, które są mapowane na elementy pierwotne języka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="fe326-106">The `[!OP.NO-LOC(System.Text.Json)]` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="fe326-107">Możesz pisać niestandardowe konwertery:</span><span class="sxs-lookup"><span data-stu-id="fe326-107">You can write custom converters:</span></span>

* <span data-ttu-id="fe326-108">Aby zastąpić domyślne zachowanie konwertera wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="fe326-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="fe326-109">Na przykład możesz chcieć, aby wartości `DateTime` były reprezentowane w formacie mm/dd/rrrr zamiast domyślnego formatu ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="fe326-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="fe326-110">Do obsługi niestandardowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="fe326-110">To support a custom value type.</span></span> <span data-ttu-id="fe326-111">Na przykład struktura `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="fe326-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="fe326-112">Możesz również napisać niestandardowe konwertery, aby dostosować lub zwiększyć `[!OP.NO-LOC(System.Text.Json)]` z funkcjami niezawartymi w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="fe326-112">You can also write custom converters to customize or extend `[!OP.NO-LOC(System.Text.Json)]` with functionality not included in the current release.</span></span> <span data-ttu-id="fe326-113">Poniższe scenariusze zostały omówione w dalszej części tego artykułu:</span><span class="sxs-lookup"><span data-stu-id="fe326-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="fe326-114">[Deserializacja wywnioskowanych typów do właściwości obiektu](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="fe326-114">[Deserialize inferred types to object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="fe326-115">[Obsługa słownika z kluczem niebędącym ciągiem](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="fe326-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="fe326-116">[Obsługa deserializacji polimorficznej](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="fe326-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="fe326-117">Wzorce niestandardowego konwertera</span><span class="sxs-lookup"><span data-stu-id="fe326-117">Custom converter patterns</span></span>

<span data-ttu-id="fe326-118">Istnieją dwa wzorce do tworzenia niestandardowego konwertera: wzorzec podstawowy i wzorzec fabryki.</span><span class="sxs-lookup"><span data-stu-id="fe326-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="fe326-119">Wzorzec fabryki jest przeznaczony dla konwerterów, które obsługują typ `Enum` lub otwierają typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="fe326-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="fe326-120">Wzorzec podstawowy dotyczy typów ogólnych nieogólnych i zamkniętych.</span><span class="sxs-lookup"><span data-stu-id="fe326-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="fe326-121">Na przykład konwertery dla następujących typów wymagają wzorca fabryki:</span><span class="sxs-lookup"><span data-stu-id="fe326-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="fe326-122">Niektóre przykłady typów, które mogą być obsługiwane przez wzorzec Basic, obejmują:</span><span class="sxs-lookup"><span data-stu-id="fe326-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="fe326-123">Wzorzec podstawowy tworzy klasę, która może obsługiwać jeden typ.</span><span class="sxs-lookup"><span data-stu-id="fe326-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="fe326-124">Wzorzec fabryki tworzy klasę, która określa w czasie wykonywania, który określony typ jest wymagany i dynamicznie tworzy odpowiedni konwerter.</span><span class="sxs-lookup"><span data-stu-id="fe326-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="fe326-125">Przykładowy konwerter podstawowy</span><span class="sxs-lookup"><span data-stu-id="fe326-125">Sample basic converter</span></span>

<span data-ttu-id="fe326-126">Poniższy przykład to konwerter, który zastąpi domyślną serializację dla istniejącego typu danych.</span><span class="sxs-lookup"><span data-stu-id="fe326-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="fe326-127">Konwerter używa formatu mm/dd/rrrr do `DateTimeOffset` właściwości.</span><span class="sxs-lookup"><span data-stu-id="fe326-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DateTimeOffsetConverter.cs)]

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="fe326-128">Przykładowy konwerter wzorców fabryki</span><span class="sxs-lookup"><span data-stu-id="fe326-128">Sample factory pattern converter</span></span>

<span data-ttu-id="fe326-129">Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="fe326-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="fe326-130">Kod jest zgodny ze wzorcem fabryki, ponieważ pierwszy parametr typu ogólnego to `Enum`, a drugi jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="fe326-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="fe326-131">Metoda `CanConvert` zwraca `true` tylko dla `Dictionary` z dwoma parametrami ogólnymi, z których pierwszy jest typem `Enum`.</span><span class="sxs-lookup"><span data-stu-id="fe326-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="fe326-132">Wewnętrzny konwerter pobiera istniejący konwerter do obsługi dowolnego typu w czasie wykonywania dla `TValue`.</span><span class="sxs-lookup"><span data-stu-id="fe326-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="fe326-133">Poprzedni kod jest taki sam jak w [słowniku pomocy technicznej z kluczem innym niż ciąg](#support-dictionary-with-non-string-key) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="fe326-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="fe326-134">Kroki prowadzące do wzorca podstawowego</span><span class="sxs-lookup"><span data-stu-id="fe326-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="fe326-135">Poniższe kroki wyjaśniają, jak utworzyć konwerter, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="fe326-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="fe326-136">Utwórz klasę, która pochodzi od <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverter%601>, gdzie `T` jest typem, który ma być serializowany i deserializowany.</span><span class="sxs-lookup"><span data-stu-id="fe326-136">Create a class that derives from <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="fe326-137">Zastąp metodę `Read`, aby deserializować przychodzącego pliku JSON i przekonwertować go na `T`typu.</span><span class="sxs-lookup"><span data-stu-id="fe326-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="fe326-138">Użyj <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonReader>, który jest przesyłany do metody, aby odczytać kod JSON.</span><span class="sxs-lookup"><span data-stu-id="fe326-138">Use the <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="fe326-139">Zastąp metodę `Write`, aby serializować obiekt przychodzący typu `T`.</span><span class="sxs-lookup"><span data-stu-id="fe326-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="fe326-140">Użyj <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonWriter>, który jest przesyłany do metody, aby zapisać kod JSON.</span><span class="sxs-lookup"><span data-stu-id="fe326-140">Use the <xref:[!OP.NO-LOC(System.Text.Json)].Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="fe326-141">Zastąp metodę `CanConvert` tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="fe326-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="fe326-142">Domyślna implementacja zwraca `true`, gdy typ do przekonwertowania jest typu `T`.</span><span class="sxs-lookup"><span data-stu-id="fe326-142">The default implementation returns `true` when the type to convert is of type `T`.</span></span> <span data-ttu-id="fe326-143">W związku z tym konwertery obsługujące tylko typ `T` nie muszą przesłaniać tej metody.</span><span class="sxs-lookup"><span data-stu-id="fe326-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="fe326-144">Aby zapoznać się z przykładem konwertera, który musi przesłonić tę metodę, zobacz sekcję [deserializacji polimorficzną](#support-polymorphic-deserialization) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="fe326-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="fe326-145">Możesz odwołać się do [wbudowanego kodu źródłowego konwerterów](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/src/[!OP.NO-LOC(System/Text/Json)]/Serialization/Converters/) jako implementacji odwołań do pisania konwerterów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fe326-145">You can refer to the [built-in converters source code](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/[!OP.NO-LOC(System.Text.Json)]/src/[!OP.NO-LOC(System/Text/Json)]/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="fe326-146">Kroki prowadzące do wzorca fabryki</span><span class="sxs-lookup"><span data-stu-id="fe326-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="fe326-147">Poniższe kroki wyjaśniają, jak utworzyć konwerter, postępując zgodnie z wzorcem fabryki:</span><span class="sxs-lookup"><span data-stu-id="fe326-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="fe326-148">Utwórz klasę pochodzącą z <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="fe326-148">Create a class that derives from <xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="fe326-149">Zastąp metodę `CanConvert`, aby zwracał wartość true, gdy typ do przekonwertowania jest taki, który może obsłużyć konwerter.</span><span class="sxs-lookup"><span data-stu-id="fe326-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="fe326-150">Na przykład, jeśli konwerter jest przeznaczony dla `List<T>` może obsłużyć tylko `List<int>`, `List<string>`i `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="fe326-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span>
* <span data-ttu-id="fe326-151">Zastąp metodę `CreateConverter`, aby zwracała wystąpienie klasy konwertera, która będzie obsługiwała typ do konwersji, który jest dostarczany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fe326-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="fe326-152">Utwórz klasę konwertera, którą tworzy instancja metody `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="fe326-152">Create the converter class that the `CreateConverter` method instantiates.</span></span>

<span data-ttu-id="fe326-153">Wzorzec fabryki jest wymagany do otwierania typów ogólnych, ponieważ kod do konwersji obiektu na i z ciągu nie jest taki sam dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="fe326-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="fe326-154">Konwerter dla otwartego typu ogólnego (na przykład`List<T>`) musi utworzyć konwerter dla zamkniętego typu ogólnego (na przykład`List<DateTime>`) w tle.</span><span class="sxs-lookup"><span data-stu-id="fe326-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="fe326-155">Kod musi być zapisany, aby obsługiwał każdy zamknięty typ ogólny, który może obsłużyć konwerter.</span><span class="sxs-lookup"><span data-stu-id="fe326-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="fe326-156">Typ `Enum` jest podobny do otwartego typu ogólnego: konwerter dla `Enum` musi utworzyć konwerter dla konkretnej `Enum``WeekdaysEnum`(na przykład) w tle.</span><span class="sxs-lookup"><span data-stu-id="fe326-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span>

## <a name="error-handling"></a><span data-ttu-id="fe326-157">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="fe326-157">Error handling</span></span>

<span data-ttu-id="fe326-158">Jeśli musisz zgłosić wyjątek w kodzie obsługi błędu, rozważ przegenerowanie <xref:[!OP.NO-LOC(System.Text.Json)].JsonException> bez komunikatu.</span><span class="sxs-lookup"><span data-stu-id="fe326-158">If you need to throw an exception in error-handling code, consider throwing a <xref:[!OP.NO-LOC(System.Text.Json)].JsonException> without a message.</span></span> <span data-ttu-id="fe326-159">Ten typ wyjątku powoduje automatyczne utworzenie komunikatu zawierającego ścieżkę do części JSON, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="fe326-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="fe326-160">Na przykład instrukcja `throw new JsonException();` generuje komunikat o błędzie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fe326-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```
Unhandled exception. [!OP.NO-LOC(System.Text.Json)].JsonException:
The JSON value could not be converted to System.Object.
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="fe326-161">Jeśli zostanie wyświetlony komunikat (na przykład `throw new JsonException("Error occurred")`, wyjątek nadal udostępnia ścieżkę we właściwości <xref:[!OP.NO-LOC(System.Text.Json)].JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="fe326-161">If you do provide a message (for example, `throw new JsonException("Error occurred")`, the exception still provides the path in the <xref:[!OP.NO-LOC(System.Text.Json)].JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="fe326-162">Rejestrowanie niestandardowego konwertera</span><span class="sxs-lookup"><span data-stu-id="fe326-162">Register a custom converter</span></span>

<span data-ttu-id="fe326-163">*Zarejestruj* konwerter niestandardowy, aby zastosować `Serialize` i `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="fe326-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="fe326-164">Wybierz jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="fe326-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="fe326-165">Dodaj wystąpienie klasy Converter do kolekcji <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="fe326-165">Add an instance of the converter class to the <xref:[!OP.NO-LOC(System.Text.Json)].JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="fe326-166">Zastosuj atrybut [[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) do właściwości, które wymagają konwertera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="fe326-166">Apply the [[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="fe326-167">Zastosuj atrybut [[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) do klasy lub struktury, która reprezentuje niestandardowy typ wartości.</span><span class="sxs-lookup"><span data-stu-id="fe326-167">Apply the [[JsonConverter]](xref:[!OP.NO-LOC(System.Text.Json)].Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="fe326-168">Przykład rejestracji — kolekcja konwerterów</span><span class="sxs-lookup"><span data-stu-id="fe326-168">Registration sample - Converters collection</span></span>

<span data-ttu-id="fe326-169">Oto przykład, który sprawia, że <xref:System.ComponentModel.DateTimeOffsetConverter> domyślny dla właściwości typu <xref:System.DateTimeOffset>:</span><span class="sxs-lookup"><span data-stu-id="fe326-169">Here's an example that makes the <xref:System.ComponentModel.DateTimeOffsetConverter> the default for properties of type <xref:System.DateTimeOffset>:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetSerialize)]

<span data-ttu-id="fe326-170">Załóżmy, że Serializacja wystąpienia następującego typu:</span><span class="sxs-lookup"><span data-stu-id="fe326-170">Suppose you serialize an instance of the following type:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWF)]

<span data-ttu-id="fe326-171">Oto przykład danych wyjściowych JSON, które pokazują, że użyto niestandardowego konwertera:</span><span class="sxs-lookup"><span data-stu-id="fe326-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureCelsius": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="fe326-172">Poniższy kod używa tego samego podejścia do deserializacji przy użyciu niestandardowego konwertera `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="fe326-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithConvertersCollection.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="fe326-173">Przykład rejestracji — [JsonConverter] na właściwości</span><span class="sxs-lookup"><span data-stu-id="fe326-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="fe326-174">Poniższy kod wybiera niestandardowy konwerter właściwości `Date`:</span><span class="sxs-lookup"><span data-stu-id="fe326-174">The following code selects a custom converter for the `Date` property:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithConverterAttribute)]

<span data-ttu-id="fe326-175">Kod do serializacji `WeatherForecastWithConverterAttribute` nie wymaga użycia `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="fe326-175">The code to serialize `WeatherForecastWithConverterAttribute` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetSerialize)]

<span data-ttu-id="fe326-176">Kod do deserializacji również nie wymaga użycia `Converters`:</span><span class="sxs-lookup"><span data-stu-id="fe326-176">The code to deserialize also doesn't require the use of `Converters`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RegisterConverterWithAttributeOnProperty.cs?name=SnippetDeserialize)]

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="fe326-177">Przykład rejestracji — [JsonConverter] w typie</span><span class="sxs-lookup"><span data-stu-id="fe326-177">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="fe326-178">Oto kod, który tworzy strukturę i stosuje do niej atrybut `[JsonConverter]`:</span><span class="sxs-lookup"><span data-stu-id="fe326-178">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Temperature.cs)]

<span data-ttu-id="fe326-179">Oto niestandardowy konwerter dla poprzedniej struktury:</span><span class="sxs-lookup"><span data-stu-id="fe326-179">Here's the custom converter for the preceding struct:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/TemperatureConverter.cs)]

<span data-ttu-id="fe326-180">Atrybut `[JsonConvert]` w strukturze rejestruje niestandardowy konwerter jako domyślny dla właściwości typu `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="fe326-180">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="fe326-181">Konwerter jest automatycznie używany we właściwości `TemperatureCelsius` następującego typu podczas serializacji lub deserializacji:</span><span class="sxs-lookup"><span data-stu-id="fe326-181">The converter is automatically used on the `TemperatureCelsius` property of the following type when you serialize or deserialize it:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithTemperatureStruct)]

## <a name="converter-registration-precedence"></a><span data-ttu-id="fe326-182">Pierwszeństwo rejestracji konwertera</span><span class="sxs-lookup"><span data-stu-id="fe326-182">Converter registration precedence</span></span>

<span data-ttu-id="fe326-183">Podczas serializacji lub deserializacji konwerter jest wybierany dla każdego elementu JSON w następującej kolejności, na podstawie najwyższego priorytetu:</span><span class="sxs-lookup"><span data-stu-id="fe326-183">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="fe326-184">`[JsonConverter]` zastosowana do właściwości.</span><span class="sxs-lookup"><span data-stu-id="fe326-184">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="fe326-185">Konwerter dodany do kolekcji `Converters`.</span><span class="sxs-lookup"><span data-stu-id="fe326-185">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="fe326-186">`[JsonConverter]` zastosowana do niestandardowego typu wartości lub POCO.</span><span class="sxs-lookup"><span data-stu-id="fe326-186">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="fe326-187">Jeśli wiele konwerterów niestandardowych dla typu są zarejestrowane w kolekcji `Converters`, zostanie użyty pierwszy konwerter zwracający wartość true dla `CanConvert`.</span><span class="sxs-lookup"><span data-stu-id="fe326-187">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="fe326-188">Wbudowany konwerter jest wybierany tylko wtedy, gdy nie zarejestrowano żadnego odpowiedniego konwertera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="fe326-188">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="fe326-189">Przykłady konwerterów dla typowych scenariuszy</span><span class="sxs-lookup"><span data-stu-id="fe326-189">Converter samples for common scenarios</span></span>

<span data-ttu-id="fe326-190">Poniższe sekcje zawierają przykłady konwerterów, które dotyczą niektórych typowych scenariuszy, które nie obsługują funkcji wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="fe326-190">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

* [<span data-ttu-id="fe326-191">Deserializacja wywnioskowanych typów do właściwości obiektu</span><span class="sxs-lookup"><span data-stu-id="fe326-191">Deserialize inferred types to object properties</span></span>](#deserialize-inferred-types-to-object-properties)
* [<span data-ttu-id="fe326-192">Obsługa słownika z kluczem niebędącym ciągiem</span><span class="sxs-lookup"><span data-stu-id="fe326-192">Support Dictionary with non-string key</span></span>](#support-dictionary-with-non-string-key)
* [<span data-ttu-id="fe326-193">Obsługa deserializacji polimorficzna</span><span class="sxs-lookup"><span data-stu-id="fe326-193">Support polymorphic deserialization</span></span>](#support-polymorphic-deserialization)

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="fe326-194">Deserializacja wywnioskowanych typów do właściwości obiektu</span><span class="sxs-lookup"><span data-stu-id="fe326-194">Deserialize inferred types to object properties</span></span>

<span data-ttu-id="fe326-195">Podczas deserializacji do właściwości typu `object`zostanie utworzony obiekt `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="fe326-195">When deserializing to a property of type `object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="fe326-196">Przyczyną jest to, że Deserializator nie wie, jakie typy CLR należy utworzyć, i nie próbuje go odgadnąć.</span><span class="sxs-lookup"><span data-stu-id="fe326-196">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="fe326-197">Na przykład, jeśli właściwość JSON ma wartość "true", Deserializator nie uzna, że wartość jest `Boolean`, a jeśli element ma "01/01/2019", Deserializator nie uzna, że jest to `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="fe326-197">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="fe326-198">Wnioskowanie o typie może być niedokładne.</span><span class="sxs-lookup"><span data-stu-id="fe326-198">Type inference can be inaccurate.</span></span> <span data-ttu-id="fe326-199">Jeśli Deserializator analizuje numer JSON, który nie ma punktu dziesiętnego jako `long`, co może spowodować problemy poza zakresem, jeśli wartość została pierwotnie zserializowana jako `ulong` lub `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="fe326-199">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="fe326-200">Analizowanie liczby, która ma przecinek dziesiętny jako `double` może stracić dokładnooć, jeśli liczba została pierwotnie zserializowana jako `decimal`.</span><span class="sxs-lookup"><span data-stu-id="fe326-200">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="fe326-201">W przypadku scenariuszy, które wymagają wnioskowania o typie, poniższy kod przedstawia niestandardowy konwerter dla `object` właściwości.</span><span class="sxs-lookup"><span data-stu-id="fe326-201">For scenarios that require type inference, the following code shows a custom converter for `object` properties.</span></span> <span data-ttu-id="fe326-202">Kod konwertuje:</span><span class="sxs-lookup"><span data-stu-id="fe326-202">The code converts:</span></span>

* <span data-ttu-id="fe326-203">`true` i `false` do `Boolean`</span><span class="sxs-lookup"><span data-stu-id="fe326-203">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="fe326-204">Liczby bez wartości dziesiętnej do `long`</span><span class="sxs-lookup"><span data-stu-id="fe326-204">Numbers without a decimal to `long`</span></span>
* <span data-ttu-id="fe326-205">Liczby z liczbą dziesiętną do `double`</span><span class="sxs-lookup"><span data-stu-id="fe326-205">Numbers with a decimal to `double`</span></span>
* <span data-ttu-id="fe326-206">Daty do `DateTime`</span><span class="sxs-lookup"><span data-stu-id="fe326-206">Dates to `DateTime`</span></span>
* <span data-ttu-id="fe326-207">Ciągi do `string`</span><span class="sxs-lookup"><span data-stu-id="fe326-207">Strings to `string`</span></span>
* <span data-ttu-id="fe326-208">Wszystkie inne elementy do `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="fe326-208">Everything else to `JsonElement`</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/ObjectToInferredTypesConverter.cs)]

<span data-ttu-id="fe326-209">Następujący kod rejestruje konwerter:</span><span class="sxs-lookup"><span data-stu-id="fe326-209">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DeserializeInferredTypesToObject.cs?name=SnippetRegister)]

<span data-ttu-id="fe326-210">Oto przykładowy typ z właściwościami `object`:</span><span class="sxs-lookup"><span data-stu-id="fe326-210">Here's an example type with `object` properties:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithObjectProperties)]

<span data-ttu-id="fe326-211">Poniższy przykład JSON do deserializacji zawiera wartości, które zostaną rozszeregowane jako `DateTime`, `long`i `string`:</span><span class="sxs-lookup"><span data-stu-id="fe326-211">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="fe326-212">Bez niestandardowego konwertera deserializacja umieszcza `JsonElement` w każdej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fe326-212">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="fe326-213">[Folder testów jednostkowych](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują deserializacji do właściwości `object`.</span><span class="sxs-lookup"><span data-stu-id="fe326-213">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to `object` properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="fe326-214">Obsługa słownika z kluczem niebędącym ciągiem</span><span class="sxs-lookup"><span data-stu-id="fe326-214">Support Dictionary with non-string key</span></span>

<span data-ttu-id="fe326-215">Wbudowana obsługa kolekcji słowników ma na celu `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="fe326-215">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="fe326-216">Oznacza to, że klucz musi być ciągiem.</span><span class="sxs-lookup"><span data-stu-id="fe326-216">That is, the key must be a string.</span></span> <span data-ttu-id="fe326-217">Aby zapewnić obsługę słownika z liczbą całkowitą lub innym typem jako klucz, wymagany jest konwerter niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="fe326-217">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="fe326-218">Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="fe326-218">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/DictionaryTKeyEnumTValueConverter.cs)]

<span data-ttu-id="fe326-219">Następujący kod rejestruje konwerter:</span><span class="sxs-lookup"><span data-stu-id="fe326-219">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripDictionaryTkeyEnumTValue.cs?name=SnippetRegister)]

<span data-ttu-id="fe326-220">Konwerter może serializować i deserializować Właściwość `TemperatureRanges` poniższej klasy, która używa następujących `Enum`:</span><span class="sxs-lookup"><span data-stu-id="fe326-220">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/WeatherForecast.cs?name=SnippetWFWithEnumDictionary)]

<span data-ttu-id="fe326-221">Dane wyjściowe JSON z serializacji wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fe326-221">The JSON output from serialization looks like the following example:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureCelsius": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="fe326-222">[Folder testy jednostkowe](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują słowniki niebędące ciągami.</span><span class="sxs-lookup"><span data-stu-id="fe326-222">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="fe326-223">Obsługa deserializacji polimorficzna</span><span class="sxs-lookup"><span data-stu-id="fe326-223">Support polymorphic deserialization</span></span>

<span data-ttu-id="fe326-224">Wbudowane funkcje zapewniają ograniczony zakres [serializacji polimorficznej](system-text-json-how-to.md#serialize-properties-of-derived-classes) , ale nie obsługują deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe326-224">Built-in features provide a limited range of [polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) but no support for deserialization at all.</span></span> <span data-ttu-id="fe326-225">Deserializacja wymaga konwertera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="fe326-225">Deserialization requires a custom converter.</span></span>

<span data-ttu-id="fe326-226">Załóżmy na przykład, że masz `Person` abstrakcyjną klasę bazową z `Employee` i `Customer` klasami pochodnymi.</span><span class="sxs-lookup"><span data-stu-id="fe326-226">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="fe326-227">Deserializacja polimorficzna oznacza, że w czasie projektowania można określić `Person` jako element docelowy deserializacji, a `Customer` i `Employee` obiektów w formacie JSON są prawidłowo deserializowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="fe326-227">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="fe326-228">Podczas deserializacji należy znaleźć wskazówki, które identyfikują wymagany typ w kodzie JSON.</span><span class="sxs-lookup"><span data-stu-id="fe326-228">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="fe326-229">Rodzaje dostępnych wskazówek różnią się w zależności od scenariusza.</span><span class="sxs-lookup"><span data-stu-id="fe326-229">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="fe326-230">Na przykład może być dostępna właściwość rozróżniacza lub może zależeć od obecności lub braku określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="fe326-230">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="fe326-231">Bieżąca wersja `System.Text.Json` nie udostępnia atrybutów, aby określić sposób obsługi scenariuszy deserializacji polimorficznych, dlatego wymagane są niestandardowe konwertery.</span><span class="sxs-lookup"><span data-stu-id="fe326-231">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="fe326-232">Poniższy kod przedstawia klasę bazową, dwie klasy pochodne i niestandardowy konwerter dla nich.</span><span class="sxs-lookup"><span data-stu-id="fe326-232">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="fe326-233">Konwerter używa właściwości rozróżniacza do wykonywania deserializacji polimorficznej.</span><span class="sxs-lookup"><span data-stu-id="fe326-233">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="fe326-234">Rozróżniacz typu nie znajduje się w definicjach klas, ale jest tworzony podczas serializacji i jest odczytywany podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="fe326-234">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/Person.cs?name=SnippetPerson)]

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/PersonConverterWithTypeDiscriminator.cs)]

<span data-ttu-id="fe326-235">Następujący kod rejestruje konwerter:</span><span class="sxs-lookup"><span data-stu-id="fe326-235">The following code registers the converter:</span></span>

[!code-csharp[](~/samples/snippets/core/system-text-json/csharp/RoundtripPolymorphic.cs?name=SnippetRegister)]

<span data-ttu-id="fe326-236">Konwerter może deserializować kod JSON, który został utworzony przy użyciu tego samego konwertera do serializacji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="fe326-236">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

```json
[
  {
    "TypeDiscriminator": 1,
    "CreditLimit": 10000,
    "Name": "John"
  },
  {
    "TypeDiscriminator": 2,
    "OfficeNumber": "555-1234",
    "Name": "Nancy"
  }
]
```

<span data-ttu-id="fe326-237">Kod konwertera w poprzednim przykładzie odczytuje i zapisuje każdą właściwość ręcznie.</span><span class="sxs-lookup"><span data-stu-id="fe326-237">The converter code in the preceding example reads and writes each property manually.</span></span> <span data-ttu-id="fe326-238">Alternatywą jest wywołanie `Deserialize` lub `Serialize` do wykonania niektórych zadań.</span><span class="sxs-lookup"><span data-stu-id="fe326-238">An alternative is to call `Deserialize` or `Serialize` to do some of the work.</span></span> <span data-ttu-id="fe326-239">Aby zapoznać się z przykładem, zobacz [ten StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span><span class="sxs-lookup"><span data-stu-id="fe326-239">For an example, see [this StackOverflow post](https://stackoverflow.com/a/59744873/12509023).</span></span>

## <a name="other-custom-converter-samples"></a><span data-ttu-id="fe326-240">Inne przykłady konwerterów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="fe326-240">Other custom converter samples</span></span>

<span data-ttu-id="fe326-241">[Migracja z Newtonsoft.Json do System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) artykułu zawiera dodatkowe przykłady konwerterów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="fe326-241">The [Migrate from Newtonsoft.Json to System.Text.Json](system-text-json-migrate-from-newtonsoft-how-to.md) article contains additional samples of custom converters.</span></span>

<span data-ttu-id="fe326-242">[Folder testy jednostkowe](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) w `System.Text.Json.Serialization` kodzie źródłowym zawiera inne niestandardowe przykłady konwerterów, takie jak:</span><span class="sxs-lookup"><span data-stu-id="fe326-242">The [unit tests folder](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="fe326-243">[Konwerter Int32, który konwertuje wartość null na wartość 0 podczas deserializacji](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span><span class="sxs-lookup"><span data-stu-id="fe326-243">[Int32 converter that converts null to 0 on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.NullValueType.cs)</span></span>
* <span data-ttu-id="fe326-244">[Konwerter Int32, który zezwala na wartości typu String i Number przy deserializacji](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span><span class="sxs-lookup"><span data-stu-id="fe326-244">[Int32 converter that allows both string and number values on deserialize](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Int32.cs)</span></span>
* <span data-ttu-id="fe326-245">[Konwerter wyliczenia](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span><span class="sxs-lookup"><span data-stu-id="fe326-245">[Enum converter](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Enum.cs)</span></span>
* <span data-ttu-id="fe326-246">[Listowy konwerter\<T > akceptujący dane zewnętrzne](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span><span class="sxs-lookup"><span data-stu-id="fe326-246">[List\<T> converter that accepts external data](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.List.cs)</span></span>
* <span data-ttu-id="fe326-247">[Długi konwerter [], który działa z rozdzielaną przecinkami listą liczb](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span><span class="sxs-lookup"><span data-stu-id="fe326-247">[Long[] converter that works with a comma-delimited list of numbers](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/tests/Serialization/CustomConverterTests.Array.cs)</span></span>

<span data-ttu-id="fe326-248">Jeśli musisz utworzyć konwerter, który modyfikuje zachowanie istniejącego wbudowanego konwertera, możesz uzyskać [kod źródłowy istniejącego konwertera](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) , który będzie używany jako punkt wyjścia do dostosowania.</span><span class="sxs-lookup"><span data-stu-id="fe326-248">If you need to make a converter that modifies the behavior of an existing built-in converter, you can get [the source code of the existing converter](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters) to serve as a starting point for customization.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="fe326-249">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="fe326-249">Additional resources</span></span>

* <span data-ttu-id="fe326-250">[Kod źródłowy wbudowanych konwerterów](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span><span class="sxs-lookup"><span data-stu-id="fe326-250">[Source code for built-in converters](https://github.com/dotnet/runtime/tree/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/src/System/Text/Json/Serialization/Converters)</span></span>
* <span data-ttu-id="fe326-251">[Obsługa DateTime i DateTimeOffset w System.Text.Json](../datetime/system-text-json-support.md)</span><span class="sxs-lookup"><span data-stu-id="fe326-251">[DateTime and DateTimeOffset support in System.Text.Json](../datetime/system-text-json-support.md)</span></span>
* <span data-ttu-id="fe326-252">[Przegląd System.Text.Json](system-text-json-overview.md)</span><span class="sxs-lookup"><span data-stu-id="fe326-252">[System.Text.Json overview](system-text-json-overview.md)</span></span>
* <span data-ttu-id="fe326-253">[Jak używać System.Text.Json](system-text-json-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="fe326-253">[How to use System.Text.Json](system-text-json-how-to.md)</span></span>
* <span data-ttu-id="fe326-254">[Jak przeprowadzić migrację z Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span><span class="sxs-lookup"><span data-stu-id="fe326-254">[How to migrate from Newtonsoft.Json](system-text-json-migrate-from-newtonsoft-how-to.md)</span></span>
* <span data-ttu-id="fe326-255">[Dokumentacja interfejsu API System.Text.Json](xref:System.Text.Json)</span><span class="sxs-lookup"><span data-stu-id="fe326-255">[System.Text.Json API reference](xref:System.Text.Json)</span></span>
* <span data-ttu-id="fe326-256">[System.Text.Json. Dokumentacja interfejsu API serializacji](xref:System.Text.Json.Serialization)</span><span class="sxs-lookup"><span data-stu-id="fe326-256">[System.Text.Json.Serialization API reference](xref:System.Text.Json.Serialization)</span></span>
<!-- * [System.Text.Json roadmap](https://github.com/dotnet/runtime/blob/81bf79fd9aa75305e55abe2f7e9ef3f60624a3a1/src/libraries/System.Text.Json/roadmap/README.md)-->
