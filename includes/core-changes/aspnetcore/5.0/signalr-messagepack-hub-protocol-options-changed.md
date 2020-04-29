---
ms.openlocfilehash: 7a05f60cf1c04d3d73dadb54541254a83b4ea855
ms.sourcegitcommit: 1cb64b53eb1f253e6a3f53ca9510ef0be1fd06fe
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/29/2020
ms.locfileid: "82507096"
---
### <a name="signalr-messagepack-hub-protocol-options-type-changed"></a>Sygnalizacja: Zmieniono typ opcji protokołu MessagePack Hub

Typ opcji protokołu MessagePack sygnalizującego "ASP.NET Core" został zmieniony z `IList<MessagePack.IFormatterResolver>` na `MessagePackSerializerOptions` typ biblioteki [MessagePack](https://www.nuget.org/packages/MessagePack) .

Aby uzyskać więcej dyskusji na temat tej zmiany, zobacz [dotnet/aspnetcore # 20506](https://github.com/dotnet/aspnetcore/issues/20506).

#### <a name="version-introduced"></a>Wprowadzona wersja

5,0 wersja zapoznawcza 4

#### <a name="old-behavior"></a>Stare zachowanie

Możesz dodać do opcji, jak pokazano w następującym przykładzie:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers.Add(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

I Zastąp opcje w następujący sposób:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.FormatterResolvers = new List<MessagePack.IFormatterResolver>()
        {
            MessagePack.Resolvers.StandardResolver.Instance
        };
    });
```

#### <a name="new-behavior"></a>Nowe zachowanie

Możesz dodać do opcji, jak pokazano w następującym przykładzie:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions =
            options.SerializeOptions.WithResolver(MessagePack.Resolvers.StandardResolver.Instance);
    });
```

I Zastąp opcje w następujący sposób:

```csharp
services.AddSignalR()
    .AddMessagePackProtocol(options =>
    {
        options.SerializerOptions = MessagePackSerializerOptions
                .Standard
                .WithResolver(MessagePack.Resolvers.StandardResolver.Instance)
                .WithSecurity(MessagePackSecurity.UntrustedData);
    });
```

#### <a name="reason-for-change"></a>Przyczyna zmiany

Ta zmiana jest częścią przejścia do MessagePack v2. x, która została ogłoszona w polu [ASPNET/anonse # 404](https://github.com/aspnet/Announcements/issues/404). Biblioteka v2. x dodała interfejs API opcji, który jest łatwiejszy do użycia i udostępnia więcej funkcji niż lista `MessagePack.IFormatterResolver` , która była uwidoczniona wcześniej.

#### <a name="recommended-action"></a>Zalecana akcja

Ta zmiana wpływa na wszystkich użytkowników, którzy konfigurują <xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions>wartości. Jeśli używasz protokołu ASP.NET Core sygnalizującego MessagePack i modyfikowania opcji, zaktualizuj użycie, aby użyć nowego interfejsu API opcji, jak pokazano powyżej.

#### <a name="category"></a>Kategoria

ASP.NET Core

#### <a name="affected-apis"></a>Dotyczy interfejsów API

<xref:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions?displayProperty=nameWithType>

<!--

#### Affected APIs

`T:Microsoft.AspNetCore.SignalR.MessagePackHubProtocolOptions`

-->
