---
title: Zmiany w bibliotece klas podstawowych
description: Wyświetla listę przełomowych zmian w podstawowych bibliotekach .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 8cf90ca2bc8736101c1cb8d327a93d100148937b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021831"
---
# <a name="core-net-libraries-breaking-changes"></a>Podstawowe biblioteki .NET przełamują zmiany

Podstawowe biblioteki .NET zapewniają podstawowe i inne typy ogólne używane przez program .NET Core.

Na tej stronie są udokumentowane następujące zmiany podziału:

| Przełomowa zmiana | Wprowadzono wersję |
| - | :-: |
| [Interfejsy API, które zgłaszają wersję raportu, teraz zgłaszają produkt, a nie wersję pliku](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [Niestandardowe enkoderFallbackBuffer wystąpienia nie mogą cofać się rekursywnie](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Zmiany zachowania formatowania zmiennoprzecinkowej i analizy](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [Operacje analizowania zmiennoprzecinkowego nie są już nieudane lub nie mogą paść za przepełnienie](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException przeniesiono do innego zestawu](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [NET Core 3.0 stosuje najlepsze rozwiązania unicode podczas zastępowania źle sformułowanych sekwencji bajtów UTF-8](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | 3.0 |
| [TypeDescriptionProviderAttribute przeniesiono do innego zestawu](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry nie obsługuje już archiwów o niespójnych rozmiarach wpisów](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [Typ wyjątku serializatora JSON zmieniono z JsonException na NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [Zmiana semantyki (string)null w Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [Metody JsonEncodedText.Encode mają dodatkowy argument JavaScriptEncoder](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [JsonFactoryConverter.CreateSeksorwerer zmieniony](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [Zmiany interfejsu API JsonElement](#jsonelement-api-changes) | 3.0 |
| [FieldInfo.SetValue zgłasza wyjątek dla pól statycznych, tylko init](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Pola prywatne dodane do wbudowanych typów obiektów](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Zmiana wartości domyślnej UseShellExecute](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Wersje OpenSSL w systemie macOS](#openssl-versions-on-macos) | 2.1 |
| [NieautoryzowaneaccessException generowane przez FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Rdzeń 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
