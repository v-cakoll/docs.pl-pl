---
title: Jak pisać konwertery niestandardowe na potrzeby serializacji JSON — .NET
author: tdykstra
ms.author: tdykstra
ms.date: 10/16/2019
helpviewer_keywords:
- JSON serialization
- serializing objects
- serialization
- objects, serializing
- converters
ms.openlocfilehash: 361818a0bda8863f8878b86e5fb377dc0faf5246
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73741893"
---
# <a name="how-to-write-custom-converters-for-json-serialization-in-net"></a><span data-ttu-id="e0687-102">Jak napisać niestandardowe konwertery dla serializacji JSON w programie .NET</span><span class="sxs-lookup"><span data-stu-id="e0687-102">How to write custom converters for JSON serialization in .NET</span></span>

<span data-ttu-id="e0687-103">W tym artykule pokazano, jak utworzyć niestandardowe konwertery dla klas serializacji JSON, które są dostępne w przestrzeni nazw <xref:System.Text.Json>.</span><span class="sxs-lookup"><span data-stu-id="e0687-103">This article shows how to create custom converters for the JSON serialization classes that are provided in the <xref:System.Text.Json> namespace.</span></span> <span data-ttu-id="e0687-104">Aby zapoznać się z wprowadzeniem do `System.Text.Json`, zobacz [jak serializować i deserializować kod JSON w programie .NET](system-text-json-how-to.md).</span><span class="sxs-lookup"><span data-stu-id="e0687-104">For an introduction to `System.Text.Json`, see [How to serialize and deserialize JSON in .NET](system-text-json-how-to.md).</span></span>

<span data-ttu-id="e0687-105">*Konwerter* jest klasą, która konwertuje obiekt lub wartość do i z formatu JSON.</span><span class="sxs-lookup"><span data-stu-id="e0687-105">A *converter* is a class that converts an object or a value to and from JSON.</span></span> <span data-ttu-id="e0687-106">Przestrzeń nazw `System.Text.Json` zawiera wbudowane konwertery dla większości typów pierwotnych, które są mapowane na elementy pierwotne języka JavaScript.</span><span class="sxs-lookup"><span data-stu-id="e0687-106">The `System.Text.Json` namespace has built-in converters for most primitive types that map to JavaScript primitives.</span></span> <span data-ttu-id="e0687-107">Możesz pisać niestandardowe konwertery:</span><span class="sxs-lookup"><span data-stu-id="e0687-107">You can write custom converters:</span></span>

* <span data-ttu-id="e0687-108">Aby zastąpić domyślne zachowanie konwertera wbudowanego.</span><span class="sxs-lookup"><span data-stu-id="e0687-108">To override the default behavior of a built-in converter.</span></span> <span data-ttu-id="e0687-109">Na przykład możesz chcieć, aby wartości `DateTime` były reprezentowane w formacie mm/dd/rrrr zamiast domyślnego formatu ISO 8601-1:2019.</span><span class="sxs-lookup"><span data-stu-id="e0687-109">For example, you might want `DateTime` values to be represented by mm/dd/yyyy format instead of the default  ISO 8601-1:2019 format.</span></span>
* <span data-ttu-id="e0687-110">Do obsługi niestandardowego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="e0687-110">To support a custom value type.</span></span> <span data-ttu-id="e0687-111">Na przykład struktura `PhoneNumber`.</span><span class="sxs-lookup"><span data-stu-id="e0687-111">For example, a `PhoneNumber` struct.</span></span>

<span data-ttu-id="e0687-112">Możesz również napisać niestandardowe konwertery, aby zwiększyć `System.Text.Json` z funkcjami niezawartymi w bieżącej wersji.</span><span class="sxs-lookup"><span data-stu-id="e0687-112">You can also write custom converters to extend `System.Text.Json` with functionality not included in the current release.</span></span> <span data-ttu-id="e0687-113">Poniższe scenariusze zostały omówione w dalszej części tego artykułu:</span><span class="sxs-lookup"><span data-stu-id="e0687-113">The following scenarios are covered later in this article:</span></span>

* <span data-ttu-id="e0687-114">[Deserializacja wywnioskowanych typów do właściwości obiektu](#deserialize-inferred-types-to-object-properties).</span><span class="sxs-lookup"><span data-stu-id="e0687-114">[Deserialize inferred types to Object properties](#deserialize-inferred-types-to-object-properties).</span></span>
* <span data-ttu-id="e0687-115">[Obsługa słownika z kluczem niebędącym ciągiem](#support-dictionary-with-non-string-key).</span><span class="sxs-lookup"><span data-stu-id="e0687-115">[Support Dictionary with non-string key](#support-dictionary-with-non-string-key).</span></span>
* <span data-ttu-id="e0687-116">[Obsługa deserializacji polimorficznej](#support-polymorphic-deserialization).</span><span class="sxs-lookup"><span data-stu-id="e0687-116">[Support polymorphic deserialization](#support-polymorphic-deserialization).</span></span>

## <a name="custom-converter-patterns"></a><span data-ttu-id="e0687-117">Wzorce niestandardowego konwertera</span><span class="sxs-lookup"><span data-stu-id="e0687-117">Custom converter patterns</span></span>

<span data-ttu-id="e0687-118">Istnieją dwa wzorce do tworzenia niestandardowego konwertera: wzorzec podstawowy i wzorzec fabryki.</span><span class="sxs-lookup"><span data-stu-id="e0687-118">There are two patterns for creating a custom converter: the basic pattern and the factory pattern.</span></span> <span data-ttu-id="e0687-119">Wzorzec fabryki jest przeznaczony dla konwerterów, które obsługują typ `Enum` lub otwierają typy ogólne.</span><span class="sxs-lookup"><span data-stu-id="e0687-119">The factory pattern is for converters that handle type `Enum` or open generics.</span></span> <span data-ttu-id="e0687-120">Wzorzec podstawowy dotyczy typów ogólnych nieogólnych i zamkniętych.</span><span class="sxs-lookup"><span data-stu-id="e0687-120">The basic pattern is for non-generic and closed generic types.</span></span>  <span data-ttu-id="e0687-121">Na przykład konwertery dla następujących typów wymagają wzorca fabryki:</span><span class="sxs-lookup"><span data-stu-id="e0687-121">For example, converters for the following types require the factory pattern:</span></span>

* `Dictionary<TKey, TValue>`
* `Enum`
* `List<T>`

<span data-ttu-id="e0687-122">Niektóre przykłady typów, które mogą być obsługiwane przez wzorzec Basic, obejmują:</span><span class="sxs-lookup"><span data-stu-id="e0687-122">Some examples of types that can be handled by the basic pattern include:</span></span>

* `Dictionary<int, string>`
* `WeekdaysEnum`
* `List<DateTimeOffset>`
* `DateTime`
* `Int32`

<span data-ttu-id="e0687-123">Wzorzec podstawowy tworzy klasę, która może obsługiwać jeden typ.</span><span class="sxs-lookup"><span data-stu-id="e0687-123">The basic pattern creates a class that can handle one type.</span></span> <span data-ttu-id="e0687-124">Wzorzec fabryki tworzy klasę, która określa w czasie wykonywania, który określony typ jest wymagany i dynamicznie tworzy odpowiedni konwerter.</span><span class="sxs-lookup"><span data-stu-id="e0687-124">The factory pattern creates a class that determines at runtime which specific type is required and dynamically creates the appropriate converter.</span></span>

## <a name="sample-basic-converter"></a><span data-ttu-id="e0687-125">Przykładowy konwerter podstawowy</span><span class="sxs-lookup"><span data-stu-id="e0687-125">Sample basic converter</span></span>

<span data-ttu-id="e0687-126">Poniższy przykład to konwerter, który zastąpi domyślną serializację dla istniejącego typu danych.</span><span class="sxs-lookup"><span data-stu-id="e0687-126">The following sample is a converter that overrides default serialization for an existing data type.</span></span> <span data-ttu-id="e0687-127">Konwerter używa formatu mm/dd/rrrr do `DateTimeOffset` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e0687-127">The converter uses mm/dd/yyyy format for `DateTimeOffset` properties.</span></span>

```csharp
private class ExampleDateTimeOffsetConverter : JsonConverter<DateTimeOffset>
{
    public override DateTimeOffset Read(
        ref Utf8JsonReader reader, 
        Type typeToConvert, 
        JsonSerializerOptions options)
    {
        return DateTimeOffset.ParseExact(reader.GetString(), 
            "MM/dd/yyyy", CultureInfo.InvariantCulture);
    }

    public override void Write(
        Utf8JsonWriter writer, 
        DateTimeOffset value, 
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString(
            "MM/dd/yyyy", CultureInfo.InvariantCulture));
    }
}
```

## <a name="sample-factory-pattern-converter"></a><span data-ttu-id="e0687-128">Przykładowy konwerter wzorców fabryki</span><span class="sxs-lookup"><span data-stu-id="e0687-128">Sample factory pattern converter</span></span>

<span data-ttu-id="e0687-129">Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`.</span><span class="sxs-lookup"><span data-stu-id="e0687-129">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`.</span></span> <span data-ttu-id="e0687-130">Kod jest zgodny ze wzorcem fabryki, ponieważ pierwszy parametr typu ogólnego to `Enum`, a drugi jest otwarty.</span><span class="sxs-lookup"><span data-stu-id="e0687-130">The code follows the factory pattern because the first generic type parameter is `Enum` and the second is open.</span></span> <span data-ttu-id="e0687-131">Metoda `CanConvert` zwraca `true` tylko dla `Dictionary` z dwoma parametrami ogólnymi, z których pierwszy jest typem `Enum`.</span><span class="sxs-lookup"><span data-stu-id="e0687-131">The `CanConvert` method returns `true` only for a `Dictionary` with two generic parameters, the first of which is an `Enum` type.</span></span> <span data-ttu-id="e0687-132">Wewnętrzny konwerter pobiera istniejący konwerter do obsługi dowolnego typu w czasie wykonywania dla `TValue`.</span><span class="sxs-lookup"><span data-stu-id="e0687-132">The inner converter gets an existing converter to handle whichever type is provided at runtime for `TValue`.</span></span> 

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="e0687-133">Poprzedni kod jest taki sam jak w [słowniku pomocy technicznej z kluczem innym niż ciąg](#support-dictionary-with-non-string-key) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="e0687-133">The preceding code is the same as what is shown in the [Support Dictionary with non-string key](#support-dictionary-with-non-string-key) later in this article.</span></span>

## <a name="steps-to-follow-the-basic-pattern"></a><span data-ttu-id="e0687-134">Kroki prowadzące do wzorca podstawowego</span><span class="sxs-lookup"><span data-stu-id="e0687-134">Steps to follow the basic pattern</span></span>

<span data-ttu-id="e0687-135">Poniższe kroki wyjaśniają, jak utworzyć konwerter, wykonując następujące czynności:</span><span class="sxs-lookup"><span data-stu-id="e0687-135">The following steps explain how to create a converter by following the basic pattern:</span></span>

* <span data-ttu-id="e0687-136">Utwórz klasę, która pochodzi od <xref:System.Text.Json.Serialization.JsonConverter%601>, gdzie `T` jest typem, który ma być serializowany i deserializowany.</span><span class="sxs-lookup"><span data-stu-id="e0687-136">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverter%601> where `T` is the type to be serialized and deserialized.</span></span>
* <span data-ttu-id="e0687-137">Zastąp metodę `Read`, aby deserializować przychodzącego pliku JSON i przekonwertować go na `T`typu.</span><span class="sxs-lookup"><span data-stu-id="e0687-137">Override the `Read` method to deserialize the incoming JSON and convert it to type `T`.</span></span> <span data-ttu-id="e0687-138">Użyj <xref:System.Text.Json.Utf8JsonReader>, który jest przesyłany do metody, aby odczytać kod JSON.</span><span class="sxs-lookup"><span data-stu-id="e0687-138">Use the <xref:System.Text.Json.Utf8JsonReader> that is passed to the method to read the JSON.</span></span>
* <span data-ttu-id="e0687-139">Zastąp metodę `Write`, aby serializować obiekt przychodzący typu `T`.</span><span class="sxs-lookup"><span data-stu-id="e0687-139">Override the `Write` method to serialize the incoming object of type `T`.</span></span> <span data-ttu-id="e0687-140">Użyj <xref:System.Text.Json.Utf8JsonWriter>, który jest przesyłany do metody, aby zapisać kod JSON.</span><span class="sxs-lookup"><span data-stu-id="e0687-140">Use the <xref:System.Text.Json.Utf8JsonWriter> that is passed to the method to write the JSON.</span></span>
* <span data-ttu-id="e0687-141">Zastąp metodę `CanConvert` tylko w razie potrzeby.</span><span class="sxs-lookup"><span data-stu-id="e0687-141">Override the `CanConvert` method only if necessary.</span></span> <span data-ttu-id="e0687-142">Domyślna implementacja zwraca `true`, gdy typ do przekonwertowania jest typu `T`.</span><span class="sxs-lookup"><span data-stu-id="e0687-142">The default implementation returns `true` when the type to convert is type `T`.</span></span> <span data-ttu-id="e0687-143">W związku z tym konwertery obsługujące tylko typ `T` nie muszą przesłaniać tej metody.</span><span class="sxs-lookup"><span data-stu-id="e0687-143">Therefore, converters that support only type `T` don't need to override this method.</span></span> <span data-ttu-id="e0687-144">Aby zapoznać się z przykładem konwertera, który musi przesłonić tę metodę, zobacz sekcję [deserializacji polimorficzną](#support-polymorphic-deserialization) w dalszej części tego artykułu.</span><span class="sxs-lookup"><span data-stu-id="e0687-144">For an example of a converter that does need to override this method, see the [polymorphic deserialization](#support-polymorphic-deserialization) section later in this article.</span></span>

<span data-ttu-id="e0687-145">Możesz odwołać się do [wbudowanego kodu źródłowego konwerterów](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) jako implementacji odwołań do pisania konwerterów niestandardowych.</span><span class="sxs-lookup"><span data-stu-id="e0687-145">You can refer to the [built-in converters source code](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/) as reference implementations for writing custom converters.</span></span>

## <a name="steps-to-follow-the-factory-pattern"></a><span data-ttu-id="e0687-146">Kroki prowadzące do wzorca fabryki</span><span class="sxs-lookup"><span data-stu-id="e0687-146">Steps to follow the factory pattern</span></span>

<span data-ttu-id="e0687-147">Poniższe kroki wyjaśniają, jak utworzyć konwerter, postępując zgodnie z wzorcem fabryki:</span><span class="sxs-lookup"><span data-stu-id="e0687-147">The following steps explain how to create a converter by following the factory pattern:</span></span>

* <span data-ttu-id="e0687-148">Utwórz klasę pochodzącą z <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span><span class="sxs-lookup"><span data-stu-id="e0687-148">Create a class that derives from <xref:System.Text.Json.Serialization.JsonConverterFactory>.</span></span>
* <span data-ttu-id="e0687-149">Zastąp metodę `CanConvert`, aby zwracał wartość true, gdy typ do przekonwertowania jest taki, który może obsłużyć konwerter.</span><span class="sxs-lookup"><span data-stu-id="e0687-149">Override the `CanConvert` method to return true when the type to convert is one that the converter can handle.</span></span> <span data-ttu-id="e0687-150">Na przykład, jeśli konwerter jest przeznaczony dla `List<T>` może obsłużyć tylko `List<int>`, `List<string>`i `List<DateTime>`.</span><span class="sxs-lookup"><span data-stu-id="e0687-150">For example, if the converter is for `List<T>` it might only handle `List<int>`, `List<string>`, and `List<DateTime>`.</span></span> 
* <span data-ttu-id="e0687-151">Zastąp metodę `CreateConverter`, aby zwracała wystąpienie klasy konwertera, która będzie obsługiwała typ do konwersji, który jest dostarczany w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e0687-151">Override the `CreateConverter` method to return an instance of a converter class that will handle the type-to-convert that is provided at runtime.</span></span>
* <span data-ttu-id="e0687-152">Utwórz klasę konwertera, którą tworzy instancja metody `CreateConverter`.</span><span class="sxs-lookup"><span data-stu-id="e0687-152">Create the converter class that the `CreateConverter` method instantiates.</span></span> 

<span data-ttu-id="e0687-153">Wzorzec fabryki jest wymagany do otwierania typów ogólnych, ponieważ kod do konwersji obiektu na i z ciągu nie jest taki sam dla wszystkich typów.</span><span class="sxs-lookup"><span data-stu-id="e0687-153">The factory pattern is required for open generics because the code to convert an object to and from a string isn't the same for all types.</span></span> <span data-ttu-id="e0687-154">Konwerter dla otwartego typu ogólnego (na przykład`List<T>`) musi utworzyć konwerter dla zamkniętego typu ogólnego (na przykład`List<DateTime>`) w tle.</span><span class="sxs-lookup"><span data-stu-id="e0687-154">A converter for an open generic type (`List<T>`, for example) has to create a converter for a closed generic type (`List<DateTime>`, for example) behind the scenes.</span></span> <span data-ttu-id="e0687-155">Kod musi być zapisany, aby obsługiwał każdy zamknięty typ ogólny, który może obsłużyć konwerter.</span><span class="sxs-lookup"><span data-stu-id="e0687-155">Code must be written to handle each closed-generic type that the converter can handle.</span></span>

<span data-ttu-id="e0687-156">Typ `Enum` jest podobny do otwartego typu ogólnego: konwerter dla `Enum` musi utworzyć konwerter dla konkretnej `Enum``WeekdaysEnum`(na przykład) w tle.</span><span class="sxs-lookup"><span data-stu-id="e0687-156">The `Enum` type is similar to an open generic type: a converter for `Enum` has to create a converter for a specific `Enum` (`WeekdaysEnum`, for example) behind the scenes.</span></span> 

## <a name="error-handling"></a><span data-ttu-id="e0687-157">Obsługa błędów</span><span class="sxs-lookup"><span data-stu-id="e0687-157">Error handling</span></span>

<span data-ttu-id="e0687-158">Jeśli musisz zgłosić wyjątek w kodzie obsługi błędu, rozważ przegenerowanie <xref:System.Text.Json.JsonException> bez komunikatu.</span><span class="sxs-lookup"><span data-stu-id="e0687-158">If you need to throw an exception in error-handling code, consider throwing a <xref:System.Text.Json.JsonException> without a message.</span></span> <span data-ttu-id="e0687-159">Ten typ wyjątku powoduje automatyczne utworzenie komunikatu zawierającego ścieżkę do części JSON, która spowodowała błąd.</span><span class="sxs-lookup"><span data-stu-id="e0687-159">This exception type automatically creates a message that includes the path to the part of the JSON that caused the error.</span></span> <span data-ttu-id="e0687-160">Na przykład instrukcja `throw new JsonException();` generuje komunikat o błędzie, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e0687-160">For example, the statement `throw new JsonException();` produces an error message like the following example:</span></span>

```text
Unhandled exception. System.Text.Json.JsonException: 
The JSON value could not be converted to System.Object. 
Path: $.Date | LineNumber: 1 | BytePositionInLine: 37.
```

<span data-ttu-id="e0687-161">Jeśli zostanie wyświetlony komunikat (na przykład `throw new JsonException("Error occurred)`, wyjątek nadal udostępnia ścieżkę we właściwości <xref:System.Text.Json.JsonException.Path>.</span><span class="sxs-lookup"><span data-stu-id="e0687-161">If you do provide a message (for example, `throw new JsonException("Error occurred)`, the exception still provides the path in the <xref:System.Text.Json.JsonException.Path> property.</span></span>

## <a name="register-a-custom-converter"></a><span data-ttu-id="e0687-162">Rejestrowanie niestandardowego konwertera</span><span class="sxs-lookup"><span data-stu-id="e0687-162">Register a custom converter</span></span>

<span data-ttu-id="e0687-163">*Zarejestruj* konwerter niestandardowy, aby zastosować `Serialize` i `Deserialize` metody.</span><span class="sxs-lookup"><span data-stu-id="e0687-163">*Register* a custom converter to make the `Serialize` and `Deserialize` methods use it.</span></span> <span data-ttu-id="e0687-164">Wybierz jedną z następujących metod:</span><span class="sxs-lookup"><span data-stu-id="e0687-164">Choose one of the following approaches:</span></span>

* <span data-ttu-id="e0687-165">Dodaj wystąpienie klasy Converter do kolekcji <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="e0687-165">Add an instance of the converter class to the <xref:System.Text.Json.JsonSerializerOptions.Converters?displayProperty=nameWithType> collection.</span></span>
* <span data-ttu-id="e0687-166">Zastosuj atrybut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) do właściwości, które wymagają konwertera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="e0687-166">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to the properties that require the custom converter.</span></span>
* <span data-ttu-id="e0687-167">Zastosuj atrybut [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) do klasy lub struktury, która reprezentuje niestandardowy typ wartości.</span><span class="sxs-lookup"><span data-stu-id="e0687-167">Apply the [[JsonConverter]](xref:System.Text.Json.Serialization.JsonConverterAttribute) attribute to a class or a struct that represents a custom value type.</span></span>

## <a name="registration-sample---converters-collection"></a><span data-ttu-id="e0687-168">Przykład rejestracji — kolekcja konwerterów</span><span class="sxs-lookup"><span data-stu-id="e0687-168">Registration sample - Converters collection</span></span> 

<span data-ttu-id="e0687-169">Oto przykład, który sprawia, że `ExampleDateTimeOffsetConverter` domyślny dla właściwości typu `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="e0687-169">Here's an example that makes the `ExampleDateTimeOffsetConverter` the default for properties of type `DateTimeOffset`:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
string json = JsonSerializer.Serialize(weatherForecast, options);
```

<span data-ttu-id="e0687-170">Załóżmy, że serializowany został następujący typ:</span><span class="sxs-lookup"><span data-stu-id="e0687-170">Suppose you serialize the following type:</span></span>

```csharp
class WeatherForecast
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="e0687-171">Oto przykład danych wyjściowych JSON, które pokazują, że użyto niestandardowego konwertera:</span><span class="sxs-lookup"><span data-stu-id="e0687-171">Here's an example of JSON output that shows the custom converter was used:</span></span>

```json
{
  "Date": "08/01/2019",
  "TemperatureC": 25,
  "Summary": "Hot"
}
```

<span data-ttu-id="e0687-172">Poniższy kod używa tego samego podejścia do deserializacji przy użyciu niestandardowego konwertera `DateTimeOffset`:</span><span class="sxs-lookup"><span data-stu-id="e0687-172">The following code uses the same approach to deserialize using the custom `DateTimeOffset` converter:</span></span>

```csharp
//...
JsonSerializerOptions options = new JsonSerializerOptions();
options.Converters.Add(new ExampleDateTimeOffsetConverter());
weatherForecast = JsonSerializer.Deserialize<WeatherForecast>(json, options);
```

## <a name="registration-sample---jsonconverter-on-a-property"></a><span data-ttu-id="e0687-173">Przykład rejestracji — [JsonConverter] na właściwości</span><span class="sxs-lookup"><span data-stu-id="e0687-173">Registration sample - [JsonConverter] on a property</span></span>

<span data-ttu-id="e0687-174">Poniższy kod wybiera niestandardowy konwerter właściwości `Date`:</span><span class="sxs-lookup"><span data-stu-id="e0687-174">The following code selects a custom converter for the `Date` property:</span></span>

```csharp
class WeatherForecastWithConverter
{
    [JsonConverter(typeof(ExampleDateTimeOffsetConverter))]
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

<span data-ttu-id="e0687-175">Kod do serializacji i deserializacji `WeatherForecastWithConverter` nie wymaga użycia `JsonSerializeOptions.Converters`:</span><span class="sxs-lookup"><span data-stu-id="e0687-175">The code to serialize and deserialize `WeatherForecastWithConverter` doesn't require the use of `JsonSerializeOptions.Converters`:</span></span>

```csharp
string json = JsonSerializer.Serialize(weatherForecastWithConverter);
```

```csharp
weatherForecast = JsonSerializer.Deserialize<WeatherForecastWithConverter>(json);
```

## <a name="registration-sample---jsonconverter-on-a-type"></a><span data-ttu-id="e0687-176">Przykład rejestracji — [JsonConverter] w typie</span><span class="sxs-lookup"><span data-stu-id="e0687-176">Registration sample - [JsonConverter] on a type</span></span>

<span data-ttu-id="e0687-177">Oto kod, który tworzy strukturę i stosuje do niej atrybut `[JsonConverter]`:</span><span class="sxs-lookup"><span data-stu-id="e0687-177">Here's code that creates a struct and applies the `[JsonConverter]` attribute to it:</span></span>

```csharp
[JsonConverter(typeof(TemperatureConverter))]
public struct Temperature
{
    public Temperature(int degrees, bool celsius)
    {
        _degrees = degrees;
        _isCelsius = celsius;
    }
    private bool _isCelsius;
    private int _degrees;
    public int Degrees => _degrees;
    public bool IsCelsius => _isCelsius; 
    public bool IsFahrenheit => !_isCelsius;
    public override string ToString() =>
        $"{_degrees.ToString()}{(_isCelsius ? "C" : "F")}";
    public static Temperature Parse(string input)
    {
        int degrees = int.Parse(input.Substring(0, input.Length - 1));
        bool celsius = (input.Substring(input.Length - 1) == "C");
        return new Temperature(degrees, celsius);
    }
}
```

<span data-ttu-id="e0687-178">Oto niestandardowy konwerter dla poprzedniej struktury:</span><span class="sxs-lookup"><span data-stu-id="e0687-178">Here's the custom converter for the preceding struct:</span></span>

```csharp
public class TemperatureConverter : JsonConverter<Temperature>
{
    public override Temperature Read(
        ref Utf8JsonReader reader,
        Type typeToConvert,
        JsonSerializerOptions options)
    {
        Debug.Assert(typeToConvert == typeof(Temperature));
        return Temperature.Parse(reader.GetString());
    }

    public override void Write(
        Utf8JsonWriter writer,
        Temperature value,
        JsonSerializerOptions options)
    {
        writer.WriteStringValue(value.ToString());
    }
}
```

<span data-ttu-id="e0687-179">Atrybut `[JsonConvert]` w strukturze rejestruje niestandardowy konwerter jako domyślny dla właściwości typu `Temperature`.</span><span class="sxs-lookup"><span data-stu-id="e0687-179">The `[JsonConvert]` attribute on the struct registers the custom converter as the default for properties of type `Temperature`.</span></span> <span data-ttu-id="e0687-180">Konwerter jest automatycznie używany we właściwości `TemperatureC` następującego typu podczas serializacji lub deserializacji:</span><span class="sxs-lookup"><span data-stu-id="e0687-180">The converter is automatically used on the `TemperatureC` property of the following type when you serialize or deserialize it:</span></span>

```csharp
class WeatherForecastWithTemperatureStruct
{
    public DateTimeOffset Date { get; set; }
    public Temperature TemperatureC { get; set; }
    public string Summary { get; set; }
}
```

## <a name="converter-registration-precedence"></a><span data-ttu-id="e0687-181">Pierwszeństwo rejestracji konwertera</span><span class="sxs-lookup"><span data-stu-id="e0687-181">Converter registration precedence</span></span>

<span data-ttu-id="e0687-182">Podczas serializacji lub deserializacji konwerter jest wybierany dla każdego elementu JSON w następującej kolejności, na podstawie najwyższego priorytetu:</span><span class="sxs-lookup"><span data-stu-id="e0687-182">During serialization or deserialization, a converter is chosen for each JSON element in the following order, listed from highest priority to lowest:</span></span>

* <span data-ttu-id="e0687-183">`[JsonConverter]` zastosowana do właściwości.</span><span class="sxs-lookup"><span data-stu-id="e0687-183">`[JsonConverter]` applied to a property.</span></span>
* <span data-ttu-id="e0687-184">Konwerter dodany do kolekcji `Converters`.</span><span class="sxs-lookup"><span data-stu-id="e0687-184">A converter added to the `Converters` collection.</span></span>
* <span data-ttu-id="e0687-185">`[JsonConverter]` zastosowana do niestandardowego typu wartości lub POCO.</span><span class="sxs-lookup"><span data-stu-id="e0687-185">`[JsonConverter]` applied to a custom value type or POCO.</span></span>

<span data-ttu-id="e0687-186">Jeśli wiele konwerterów niestandardowych dla typu są zarejestrowane w kolekcji `Converters`, zostanie użyty pierwszy konwerter zwracający wartość true dla `CanConvert`.</span><span class="sxs-lookup"><span data-stu-id="e0687-186">If multiple custom converters for a type are registered in the `Converters` collection, the first converter that returns true for `CanConvert` is used.</span></span>

<span data-ttu-id="e0687-187">Wbudowany konwerter jest wybierany tylko wtedy, gdy nie zarejestrowano żadnego odpowiedniego konwertera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="e0687-187">A built-in converter is chosen only if no applicable custom converter is registered.</span></span>

## <a name="converter-samples-for-common-scenarios"></a><span data-ttu-id="e0687-188">Przykłady konwerterów dla typowych scenariuszy</span><span class="sxs-lookup"><span data-stu-id="e0687-188">Converter samples for common scenarios</span></span>

<span data-ttu-id="e0687-189">Poniższe sekcje zawierają przykłady konwerterów, które dotyczą niektórych typowych scenariuszy, które nie obsługują funkcji wbudowanych.</span><span class="sxs-lookup"><span data-stu-id="e0687-189">The following sections provide converter samples that address some common scenarios that built-in functionality doesn't handle.</span></span>

### <a name="deserialize-inferred-types-to-object-properties"></a><span data-ttu-id="e0687-190">Deserializacja wywnioskowanych typów do właściwości obiektu</span><span class="sxs-lookup"><span data-stu-id="e0687-190">Deserialize inferred types to Object properties</span></span>

<span data-ttu-id="e0687-191">Podczas deserializacji do właściwości typu `Object`zostanie utworzony obiekt `JsonElement`.</span><span class="sxs-lookup"><span data-stu-id="e0687-191">When deserializing to a property of type `Object`, a `JsonElement` object is created.</span></span> <span data-ttu-id="e0687-192">Przyczyną jest to, że Deserializator nie wie, jakie typy CLR należy utworzyć, i nie próbuje go odgadnąć.</span><span class="sxs-lookup"><span data-stu-id="e0687-192">The reason is that the deserializer doesn't know what CLR type to create, and it doesn't try to guess.</span></span> <span data-ttu-id="e0687-193">Na przykład, jeśli właściwość JSON ma wartość "true", Deserializator nie uzna, że wartość jest `Boolean`, a jeśli element ma "01/01/2019", Deserializator nie uzna, że jest to `DateTime`.</span><span class="sxs-lookup"><span data-stu-id="e0687-193">For example, if a JSON property has "true", the deserializer doesn't infer that the value is a `Boolean`, and if an element has "01/01/2019", the deserializer doesn't infer that it's a `DateTime`.</span></span>

<span data-ttu-id="e0687-194">Wnioskowanie o typie może być niedokładne.</span><span class="sxs-lookup"><span data-stu-id="e0687-194">Type inference can be inaccurate.</span></span> <span data-ttu-id="e0687-195">Jeśli Deserializator analizuje numer JSON, który nie ma punktu dziesiętnego jako `long`, co może spowodować problemy poza zakresem, jeśli wartość została pierwotnie zserializowana jako `ulong` lub `BigInteger`.</span><span class="sxs-lookup"><span data-stu-id="e0687-195">If the deserializer parses a JSON number that has no decimal point as a `long`, that might result in out-of-range issues if the value was originally serialized as a `ulong` or `BigInteger`.</span></span> <span data-ttu-id="e0687-196">Analizowanie liczby, która ma przecinek dziesiętny jako `double` może stracić dokładnooć, jeśli liczba została pierwotnie zserializowana jako `decimal`.</span><span class="sxs-lookup"><span data-stu-id="e0687-196">Parsing a number that has a decimal point as a `double` might lose precision if the number was originally serialized as a `decimal`.</span></span>

<span data-ttu-id="e0687-197">W przypadku scenariuszy, które wymagają wnioskowania o typie, poniższy kod przedstawia niestandardowy konwerter dla `Object` właściwości.</span><span class="sxs-lookup"><span data-stu-id="e0687-197">For scenarios that require type inference, the following code shows a custom converter for `Object` properties.</span></span> <span data-ttu-id="e0687-198">Kod konwertuje:</span><span class="sxs-lookup"><span data-stu-id="e0687-198">The code converts:</span></span>

* <span data-ttu-id="e0687-199">`true` i `false` do `Boolean`</span><span class="sxs-lookup"><span data-stu-id="e0687-199">`true` and `false` to `Boolean`</span></span>
* <span data-ttu-id="e0687-200">Liczby do `long` lub `double`</span><span class="sxs-lookup"><span data-stu-id="e0687-200">Numbers to `long` or `double`</span></span>
* <span data-ttu-id="e0687-201">Daty do `DateTime`</span><span class="sxs-lookup"><span data-stu-id="e0687-201">Dates to `DateTime`</span></span>
* <span data-ttu-id="e0687-202">Ciągi do `string`</span><span class="sxs-lookup"><span data-stu-id="e0687-202">Strings to `string`</span></span>
* <span data-ttu-id="e0687-203">Wszystkie inne elementy do `JsonElement`</span><span class="sxs-lookup"><span data-stu-id="e0687-203">Everything else to `JsonElement`</span></span>

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ObjectToInferredTypesConverter
        : JsonConverter<object>
    {
        public override object Read(
            ref Utf8JsonReader reader,
            Type typeToConvert,
            JsonSerializerOptions options)
        {
            if (reader.TokenType == JsonTokenType.True)
            {
                return true;
            }

            if (reader.TokenType == JsonTokenType.False)
            {
                return false;
            }

            if (reader.TokenType == JsonTokenType.Number)
            {
                if (reader.TryGetInt64(out long l))
                {
                    return l;
                }

                return reader.GetDouble();
            }

            if (reader.TokenType == JsonTokenType.String)
            {
                if (reader.TryGetDateTime(out DateTime datetime))
                {
                    return datetime;
                }

                return reader.GetString();
            }

            // Use JsonElement as fallback.
            // Newtonsoft uses JArray or JObject.
            using (JsonDocument document = JsonDocument.ParseValue(ref reader))
            {
                return document.RootElement.Clone();
            }
        }

        public override void Write(
            Utf8JsonWriter writer,
            object value,
            JsonSerializerOptions options)
        {
            throw new InvalidOperationException("Should not get here.");
        }
    }
}
```

<span data-ttu-id="e0687-204">Następujący kod rejestruje konwerter:</span><span class="sxs-lookup"><span data-stu-id="e0687-204">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new ObjectToInferredTypesConverter());
```

<span data-ttu-id="e0687-205">Oto przykładowy typ z właściwością Object:</span><span class="sxs-lookup"><span data-stu-id="e0687-205">Here's an example type with an Object property:</span></span>

```csharp
public class WeatherForecastWithObjectProperties
{
    public object Date { get; set; }
    public object TemperatureC { get; set; }
    public object Summary { get; set; }
}
```

<span data-ttu-id="e0687-206">Poniższy przykład JSON do deserializacji zawiera wartości, które zostaną rozszeregowane jako `DateTime`, `long`i `string`:</span><span class="sxs-lookup"><span data-stu-id="e0687-206">The following example of JSON to deserialize contains values that will be deserialized as `DateTime`, `long`, and `string`:</span></span>

```json
{
  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
}
```

<span data-ttu-id="e0687-207">Bez niestandardowego konwertera deserializacja umieszcza `JsonElement` w każdej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e0687-207">Without the custom converter, deserialization puts a `JsonElement` in each property.</span></span>

<span data-ttu-id="e0687-208">[Folder testów jednostkowych](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują deserializacji do właściwości obiektu.</span><span class="sxs-lookup"><span data-stu-id="e0687-208">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle deserialization to Object properties.</span></span>

### <a name="support-dictionary-with-non-string-key"></a><span data-ttu-id="e0687-209">Obsługa słownika z kluczem niebędącym ciągiem</span><span class="sxs-lookup"><span data-stu-id="e0687-209">Support Dictionary with non-string key</span></span>

<span data-ttu-id="e0687-210">Wbudowana obsługa kolekcji słowników ma na celu `Dictionary<string, TValue>`.</span><span class="sxs-lookup"><span data-stu-id="e0687-210">The built-in support for dictionary collections is for `Dictionary<string, TValue>`.</span></span> <span data-ttu-id="e0687-211">Oznacza to, że klucz musi być ciągiem.</span><span class="sxs-lookup"><span data-stu-id="e0687-211">That is, the key must be a string.</span></span> <span data-ttu-id="e0687-212">Aby zapewnić obsługę słownika z liczbą całkowitą lub innym typem jako klucz, wymagany jest konwerter niestandardowy.</span><span class="sxs-lookup"><span data-stu-id="e0687-212">To support a dictionary with an integer or some other type as the key, a custom converter is required.</span></span>

<span data-ttu-id="e0687-213">Poniższy kod przedstawia niestandardowy konwerter, który działa z `Dictionary<Enum,TValue>`:</span><span class="sxs-lookup"><span data-stu-id="e0687-213">The following code shows a custom converter that works with `Dictionary<Enum,TValue>`:</span></span>

```csharp
using System;
using System.Collections.Generic;
using System.Reflection;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class ConverterDictionaryTKeyEnumTValue : JsonConverterFactory
    {
        public override bool CanConvert(Type typeToConvert)
        {
            if (!typeToConvert.IsGenericType)
            {
                return false;
            }

            if (typeToConvert.GetGenericTypeDefinition() != typeof(Dictionary<,>))
            {
                return false;
            }

            return typeToConvert.GetGenericArguments()[0].IsEnum;
        }

        public override JsonConverter CreateConverter(
            Type type, 
            JsonSerializerOptions options)
        {
            Type keyType = type.GetGenericArguments()[0];
            Type valueType = type.GetGenericArguments()[1];

            JsonConverter converter = (JsonConverter)Activator.CreateInstance(
                typeof(DictionaryEnumConverterInner<,>).MakeGenericType(
                    new Type[] { keyType, valueType }),
                BindingFlags.Instance | BindingFlags.Public,
                binder: null,
                args: new object[] { options },
                culture: null);

            return converter;
        }

        private class DictionaryEnumConverterInner<TKey, TValue> : 
            JsonConverter<Dictionary<TKey, TValue>> where TKey : struct, Enum
        {
            private readonly JsonConverter<TValue> _valueConverter;
            private Type _keyType;
            private Type _valueType;

            public DictionaryEnumConverterInner(JsonSerializerOptions options)
            {
                // For performance, use the existing converter if available.
                _valueConverter = (JsonConverter<TValue>)options
                    .GetConverter(typeof(TValue));

                // Cache the key and value types.
                _keyType = typeof(TKey);
                _valueType = typeof(TValue);
            }

            public override Dictionary<TKey, TValue> Read(
                ref Utf8JsonReader reader, 
                Type typeToConvert, 
                JsonSerializerOptions options)
            {
                if (reader.TokenType != JsonTokenType.StartObject)
                {
                    throw new JsonException();
                }

                Dictionary<TKey, TValue> value = new Dictionary<TKey, TValue>();

                while (reader.Read())
                {
                    if (reader.TokenType == JsonTokenType.EndObject)
                    {
                        return value;
                    }

                    // Get the key.
                    if (reader.TokenType != JsonTokenType.PropertyName)
                    {
                        throw new JsonException();
                    }

                    string propertyName = reader.GetString();

                    // For performance, parse with ignoreCase:false first.
                    if (!Enum.TryParse(propertyName, ignoreCase: false, out TKey key) &&
                        !Enum.TryParse(propertyName, ignoreCase: true, out key))
                    {
                        throw new JsonException(
                            $"Unable to convert \"{propertyName}\" to Enum \"{_keyType}\".");
                    }

                    // Get the value.
                    TValue v;
                    if (_valueConverter != null)
                    {
                        reader.Read();
                        v = _valueConverter.Read(ref reader, _valueType, options);
                    }
                    else
                    {
                        v = JsonSerializer.Deserialize<TValue>(ref reader, options);
                    }

                    // Add to dictionary.
                    value.Add(key, v);
                }

                throw new JsonException();
            }

            public override void Write(
                Utf8JsonWriter writer, 
                Dictionary<TKey, TValue> value, 
                JsonSerializerOptions options)
            {
                writer.WriteStartObject();

                foreach (KeyValuePair<TKey, TValue> kvp in value)
                {
                    writer.WritePropertyName(kvp.Key.ToString());

                    if (_valueConverter != null)
                    {
                        _valueConverter.Write(writer, kvp.Value, options);
                    }
                    else
                    {
                        JsonSerializer.Serialize(writer, kvp.Value, options);
                    }
                }

                writer.WriteEndObject();
            }
        }
    }
}
```

<span data-ttu-id="e0687-214">Następujący kod rejestruje konwerter:</span><span class="sxs-lookup"><span data-stu-id="e0687-214">The following code registers the converter:</span></span>

```csharp
var serializeOptions = new JsonSerializerOptions();
serializeOptions.Converters.Add(new ConverterDictionaryTKeyEnumTValue());
```

<span data-ttu-id="e0687-215">Konwerter może serializować i deserializować Właściwość `TemperatureRanges` poniższej klasy, która używa następujących `Enum`:</span><span class="sxs-lookup"><span data-stu-id="e0687-215">The converter can serialize and deserialize the `TemperatureRanges` property of the following class that uses the following `Enum`:</span></span>

```csharp
public class WeatherForecastWithEnumDictionary
{
    public DateTimeOffset Date { get; set; }
    public int TemperatureC { get; set; }
    public string Summary { get; set; }
    public Dictionary<SummaryWordsEnum, int> TemperatureRanges { get; set; }
}

public enum SummaryWordsEnum
{
    Cold, Hot
}
```

<span data-ttu-id="e0687-216">Dane wyjściowe JSON z serializacji wyglądają podobnie jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="e0687-216">The JSON output from serialization looks like the following example:</span></span>

```json
{

  "Date": "2019-08-01T00:00:00-07:00",
  "TemperatureC": 25,
  "Summary": "Hot",
  "TemperatureRanges": {
    "Cold": 20,
    "Hot": 40
  }
}
```

<span data-ttu-id="e0687-217">[Folder testy jednostkowe](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) w przestrzeni nazw `System.Text.Json.Serialization` zawiera więcej przykładów niestandardowych konwerterów, które obsługują słowniki niebędące ciągami.</span><span class="sxs-lookup"><span data-stu-id="e0687-217">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` namespace has more examples of custom converters that handle non-string-key dictionaries.</span></span>

### <a name="support-polymorphic-deserialization"></a><span data-ttu-id="e0687-218">Obsługa deserializacji polimorficzna</span><span class="sxs-lookup"><span data-stu-id="e0687-218">Support polymorphic deserialization</span></span>

<span data-ttu-id="e0687-219">[Serializacja polimorficzna](system-text-json-how-to.md#serialize-properties-of-derived-classes) nie wymaga konwertera niestandardowego, ale deserializacja wymaga konwertera niestandardowego.</span><span class="sxs-lookup"><span data-stu-id="e0687-219">[Polymorphic serialization](system-text-json-how-to.md#serialize-properties-of-derived-classes) doesn't require a custom converter, but deserialization does require a custom converter.</span></span>

<span data-ttu-id="e0687-220">Załóżmy na przykład, że masz `Person` abstrakcyjną klasę bazową z `Employee` i `Customer` klasami pochodnymi.</span><span class="sxs-lookup"><span data-stu-id="e0687-220">Suppose, for example, you have a `Person` abstract base class, with `Employee` and `Customer` derived classes.</span></span> <span data-ttu-id="e0687-221">Deserializacja polimorficzna oznacza, że w czasie projektowania można określić `Person` jako element docelowy deserializacji, a `Customer` i `Employee` obiektów w formacie JSON są prawidłowo deserializowane w czasie wykonywania.</span><span class="sxs-lookup"><span data-stu-id="e0687-221">Polymorphic deserialization means that at design time you can specify `Person` as the deserialization target, and `Customer` and `Employee` objects in the JSON are correctly deserialized at runtime.</span></span> <span data-ttu-id="e0687-222">Podczas deserializacji należy znaleźć wskazówki, które identyfikują wymagany typ w kodzie JSON.</span><span class="sxs-lookup"><span data-stu-id="e0687-222">During deserialization, you have to find clues that identify the required type in the JSON.</span></span> <span data-ttu-id="e0687-223">Rodzaje dostępnych wskazówek różnią się w zależności od scenariusza.</span><span class="sxs-lookup"><span data-stu-id="e0687-223">The kinds of clues available vary with each scenario.</span></span> <span data-ttu-id="e0687-224">Na przykład może być dostępna właściwość rozróżniacza lub może zależeć od obecności lub braku określonej właściwości.</span><span class="sxs-lookup"><span data-stu-id="e0687-224">For example, a discriminator property might be available or you might have to rely on the presence or absence of a particular property.</span></span> <span data-ttu-id="e0687-225">Bieżąca wersja `System.Text.Json` nie udostępnia atrybutów, aby określić sposób obsługi scenariuszy deserializacji polimorficznych, dlatego wymagane są niestandardowe konwertery.</span><span class="sxs-lookup"><span data-stu-id="e0687-225">The current release of `System.Text.Json` doesn't provide attributes to specify how to handle polymorphic deserialization scenarios, so custom converters are required.</span></span>

<span data-ttu-id="e0687-226">Poniższy kod przedstawia klasę bazową, dwie klasy pochodne i niestandardowy konwerter dla nich.</span><span class="sxs-lookup"><span data-stu-id="e0687-226">The following code shows a base class, two derived classes, and a custom converter for them.</span></span> <span data-ttu-id="e0687-227">Konwerter używa właściwości rozróżniacza do wykonywania deserializacji polimorficznej.</span><span class="sxs-lookup"><span data-stu-id="e0687-227">The converter uses a discriminator property to do polymorphic deserialization.</span></span> <span data-ttu-id="e0687-228">Rozróżniacz typu nie znajduje się w definicjach klas, ale jest tworzony podczas serializacji i jest odczytywany podczas deserializacji.</span><span class="sxs-lookup"><span data-stu-id="e0687-228">The type discriminator isn't in the class definitions but is created during serialization and is read during deserialization.</span></span>

```csharp
public class Person
{
    public string Name { get; set; }
}

public class Customer : Person
{
    public decimal CreditLimit { get; set; }
}

public class Employee : Person
{
    public string OfficeNumber { get; set; }
}
```

```csharp
using System;
using System.Text.Json;
using System.Text.Json.Serialization;

namespace SystemTextJsonSamples
{
    public class PersonConverterWithTypeDiscriminator : JsonConverter<Person>
    {
        enum TypeDiscriminator
        {
            Customer = 1,
            Employee = 2
        }

        public override bool CanConvert(Type typeToConvert)
        {
            return typeof(Person).IsAssignableFrom(typeToConvert);
        }

        public override Person Read(ref Utf8JsonReader reader, Type typeToConvert, JsonSerializerOptions options)
        {
            if (reader.TokenType != JsonTokenType.StartObject)
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.PropertyName)
            {
                throw new JsonException();
            }

            string propertyName = reader.GetString();
            if (propertyName != "TypeDiscriminator")
            {
                throw new JsonException();
            }

            reader.Read();
            if (reader.TokenType != JsonTokenType.Number)
            {
                throw new JsonException();
            }

            Person value;
            TypeDiscriminator typeDiscriminator = (TypeDiscriminator)reader.GetInt32();
            switch (typeDiscriminator)
            {
                case TypeDiscriminator.Customer:
                    value = new Customer();
                    break;

                case TypeDiscriminator.Employee:
                    value = new Employee();
                    break;

                default:
                    throw new JsonException();
            }

            while (reader.Read())
            {
                if (reader.TokenType == JsonTokenType.EndObject)
                {
                    return value;
                }

                if (reader.TokenType == JsonTokenType.PropertyName)
                {
                    propertyName = reader.GetString();
                    reader.Read();
                    switch (propertyName)
                    {
                        case "CreditLimit":
                            decimal creditLimit = reader.GetDecimal();
                            ((Customer)value).CreditLimit = creditLimit;
                            break;
                        case "OfficeNumber":
                            string officeNumber = reader.GetString();
                            ((Employee)value).OfficeNumber = officeNumber;
                            break;
                        case "Name":
                            string name = reader.GetString();
                            value.Name = name;
                            break;
                    }
                }
            }

            throw new JsonException();
        }

        public override void Write(Utf8JsonWriter writer, Person value, JsonSerializerOptions options)
        {
            writer.WriteStartObject();

            if (value is Customer customer)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Customer);
                writer.WriteNumber("CreditLimit", customer.CreditLimit);
            }
            else if (value is Employee employee)
            {
                writer.WriteNumber("TypeDiscriminator", (int)TypeDiscriminator.Employee);
                writer.WriteString("OfficeNumber", employee.OfficeNumber);
            }

            writer.WriteString("Name", value.Name);

            writer.WriteEndObject();
        }
    }
}
```

<span data-ttu-id="e0687-229">Następujący kod rejestruje konwerter:</span><span class="sxs-lookup"><span data-stu-id="e0687-229">The following code registers the converter:</span></span>

```csharp
options = new JsonSerializerOptions();
options.Converters.Add(new PersonConverterWithTypeDiscriminator());
```

<span data-ttu-id="e0687-230">Konwerter może deserializować kod JSON, który został utworzony przy użyciu tego samego konwertera do serializacji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="e0687-230">The converter can deserialize JSON that was created by using the same converter to serialize, for example:</span></span>

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

## <a name="other-custom-converter-samples"></a><span data-ttu-id="e0687-231">Inne przykłady konwerterów niestandardowych</span><span class="sxs-lookup"><span data-stu-id="e0687-231">Other custom converter samples</span></span>

<span data-ttu-id="e0687-232">[Folder testy jednostkowe](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) w `System.Text.Json.Serialization` kodzie źródłowym zawiera inne niestandardowe przykłady konwerterów, takie jak:</span><span class="sxs-lookup"><span data-stu-id="e0687-232">The [unit tests folder](https://github.com/dotnet/corefx/blob/master/src/System.Text.Json/tests/Serialization/) in the `System.Text.Json.Serialization` source code includes other custom converter samples, such as:</span></span>

* <span data-ttu-id="e0687-233">konwerter `Int32`, który konwertuje wartość null na wartość 0 podczas deserializacji</span><span class="sxs-lookup"><span data-stu-id="e0687-233">`Int32` converter that converts null to 0 on deserialize</span></span>
* <span data-ttu-id="e0687-234">konwerter `Int32`, który zezwala na wartości typu String i Number przy deserializacji</span><span class="sxs-lookup"><span data-stu-id="e0687-234">`Int32` converter that allows both string and number values on deserialize</span></span>
* <span data-ttu-id="e0687-235">konwerter `Enum`</span><span class="sxs-lookup"><span data-stu-id="e0687-235">`Enum` converter</span></span>
* <span data-ttu-id="e0687-236">konwerter `List<T>`, który akceptuje dane zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="e0687-236">`List<T>` converter that accepts external data</span></span>
* <span data-ttu-id="e0687-237">konwerter `Long[]`, który współpracuje z listą liczb rozdzielanych przecinkami</span><span class="sxs-lookup"><span data-stu-id="e0687-237">`Long[]` converter that works with a comma-delimited list of numbers</span></span> 

## <a name="additional-resources"></a><span data-ttu-id="e0687-238">Dodatkowe zasoby</span><span class="sxs-lookup"><span data-stu-id="e0687-238">Additional resources</span></span>

* [<span data-ttu-id="e0687-239">System. Text. JSON — Omówienie</span><span class="sxs-lookup"><span data-stu-id="e0687-239">System.Text.Json overview</span></span>](system-text-json-overview.md)
* [<span data-ttu-id="e0687-240">Dokumentacja interfejsu API System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="e0687-240">System.Text.Json API reference</span></span>](xref:System.Text.Json)
* [<span data-ttu-id="e0687-241">Jak używać metody System. Text. JSON</span><span class="sxs-lookup"><span data-stu-id="e0687-241">How to use System.Text.Json</span></span>](system-text-json-how-to.md)
* [<span data-ttu-id="e0687-242">Kod źródłowy wbudowanych konwerterów</span><span class="sxs-lookup"><span data-stu-id="e0687-242">Source code for built-in converters</span></span>](https://github.com/dotnet/corefx/tree/master/src/System.Text.Json/src/System/Text/Json/Serialization/Converters/)
* <span data-ttu-id="e0687-243">Problemy z usługą GitHub dotyczące niestandardowych konwerterów dla `System.Text.Json`</span><span class="sxs-lookup"><span data-stu-id="e0687-243">GitHub issues related to custom converters for `System.Text.Json`</span></span>
  * [<span data-ttu-id="e0687-244">36639 wprowadzenie niestandardowych konwerterów</span><span class="sxs-lookup"><span data-stu-id="e0687-244">36639 Introducing custom converters</span></span>](https://github.com/dotnet/corefx/issues/36639)
  * [<span data-ttu-id="e0687-245">38713 informacje o deserializacji do obiektu</span><span class="sxs-lookup"><span data-stu-id="e0687-245">38713 About deserializing to Object</span></span>](https://github.com/dotnet/corefx/issues/38713)
  * [<span data-ttu-id="e0687-246">40120 dotyczące słowników kluczy niebędących ciągami</span><span class="sxs-lookup"><span data-stu-id="e0687-246">40120 About non-string-key dictionaries</span></span>](https://github.com/dotnet/corefx/issues/40120)
  * [<span data-ttu-id="e0687-247">37787 informacje o deserializacji polimorficznej</span><span class="sxs-lookup"><span data-stu-id="e0687-247">37787 About polymorphic deserialization</span></span>](https://github.com/dotnet/corefx/issues/37787)
