

# 리액트 쇼핑몰 🛒


![image](https://user-images.githubusercontent.com/34205465/189643829-f80a44e7-e35e-4e12-8a4d-955d328b6561.png)


# CODE 

#### App.js 

```

import Header from "./components/Header";
import Prototypes from "./components/Prototypes";
import Orders from "./components/Orders";
import Footer from "./components/Footer";
import AppStateProvider from "./providers/AppStateProvider";
function App() {
  return (
    <AppStateProvider>
      <Header />
      <div className="container">
        <Prototypes />
        <Orders />
        <Footer />
      </div>
    </AppStateProvider>
  );
}

export default App;

``` 


#### prototpyes 


```
/* eslint-disable */
import { useContext, useState } from "react";
import useActions from "../hooks/useAction";
import usePrototypes from "../hooks/UsePrototypes";

export default function Prototypes() {
  const prototypes = usePrototypes();
  const { addToOrder } = useActions();
  return (
    <main>
      <div className="prototypes">
        {prototypes.map((prototype) => {
          const { id, thumbnail, title, price, desc, pieUrl } = prototype;
          const click = () => {
            addToOrder(id);
          };
          return (
            <div className="prototype" key={id}>
              <a href={pieUrl} target="_BLANK" rel="noreferrer">
                <div
                  style={{
                    padding: "25px 0 33px 0 ",
                  }}
                >
                  <video
                    autoPlay
                    loop
                    playsInline
                    className="prototype__artwork prototype__edit"
                    style={{
                      objectFit: "contain",
                    }}
                    src={thumbnail}
                  />
                </div>
              </a>

              <div className="prototype__body">
                <div className="prototype__title">
                  <div
                    className="btn btn--primary float--right"
                    onClick={() => {
                      click();
                    }}
                  >
                    <i className="icon icon--plus"></i>
                  </div>
                  {title}
                </div>
                <p className="prototype__price">$ {price}</p>
                <p className="prototype__desc">{desc}</p>
              </div>
            </div>
          );
        })}{" "}
      </div>
    </main>
  );
}

```


#### Appstateprovider 


```
/* eslint-disable */
import AppStateContext from "../contexts/AppStateContext";
import { useCallback, useState } from "react";
const AppStateProvider = ({ children }) => {
  const [prototypes] = useState([
    {
      id: "pp-01",
      title: "Kids-story",
      artist: "Thomas Buisson",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/Kids-story_1.mp4",
      price: 10,
      pieUrl: "https://cloud.protopie.io/p/8a6461ad85",
    },
    {
      id: "pp-02",
      title: "mockyapp",
      artist: "Ahmed Amr",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/mockyapp.mp4",
      price: 20,
      pieUrl: "https://cloud.protopie.io/p/27631ac9d5",
    },
    {
      id: "pp-03",
      title: "macOS Folder Concept",
      artist: "Dominik Kandravý",
      desc: "Folder concept prototype by Dominik Kandravý.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/macOS_Folder_Concept_-_Folder_concept.mp4",
      price: 30,
      pieUrl: "https://cloud.protopie.io/p/acde5ccdf9",
    },
    {
      id: "pp-04",
      title: "Translator",
      artist: "Tony Kim",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/Translator.mp4",
      price: 40,
      pieUrl: "https://cloud.protopie.io/p/b91edba11d",
    },
    {
      id: "pp-05",
      title: "In-car voice control",
      artist: "Tony Kim",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/In-car_voice_control.mp4",
      price: 50,
      pieUrl: "https://cloud.protopie.io/p/6ec7e70d1a",
    },
    {
      id: "pp-06",
      title: "The Adventures of Proto",
      artist: "Richard Oldfield",
      desc: `Made exclusively for Protopie Playoff 2021
            Shout up if you get stuck!
            For the full experience. View in the Protopie App.
            #PieDay #PlayOff #ProtoPie`,
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/The_Adventures_of_Proto.mp4",
      price: 60,
      pieUrl: "https://cloud.protopie.io/p/95ee13709f",
    },
    {
      id: "pp-07",
      title: "Sunglasses shop app",
      artist: "Mustafa Alabdullah",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/sunglasses_shop_app.mp4",
      price: 70,
      pieUrl: "https://cloud.protopie.io/p/6f336cac8c",
    },
    {
      id: "pp-08",
      title: "Alwritey—Minimalist Text Editor",
      artist: "Fredo Tan",
      desc: `This minimalist text editor prototype was made with ProtoPie by Fredo Tan.
            ---
            Inspired by Writty, a simple writing app by Carlos Yllobre. Try out Writty at https://writtyapp.com.
            ---
            ProtoPie is an interactive prototyping tool for all digital products.
            ---
            Learn more about ProtoPie at https://protopie.io.`,
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/minimalist-text-editor.mp4",
      price: 80,
      pieUrl: "https://cloud.protopie.io/p/946f88f8d3",
    },
    {
      id: "pp-09",
      title: "Voice search for TV",
      artist: "Tony Kim",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/TV.mp4",
      price: 90,
      pieUrl: "https://cloud.protopie.io/p/60ee64cda0",
    },
    {
      id: "pp-10",
      title: "Finance App Visual Interaction 2.0",
      artist: "Arpit Agrawal",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/Credit_Card_App.mp4",
      price: 90,
      pieUrl:
        "https://cloud.protopie.io/p/09ce2fdf84/21?ui=true&mockup=true&touchHint=true&scaleToFit=true&cursorType=touch",
    },
    {
      id: "pp-11",
      title: "Whack-a-mole",
      artist: "Changmo Kang",
      desc: "This prototype was made with ProtoPie, the interactive prototyping tool for all digital products.",
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/Whack_a_mole.mp4",
      price: 90,
      pieUrl: "https://cloud.protopie.io/p/ab796f897e",
    },
    {
      id: "pp-12",
      title: "Voice Note",
      artist: "Haerin Song",
      desc: `Made by Haerin Song
            (Soda Design)`,
      thumbnail:
        "https://prototype-shop.s3.ap-northeast-2.amazonaws.com/thumbnails/Voice_note_with_sound_wave.mp4",
      price: 90,
      pieUrl: "https://cloud.protopie.io/p/7a0d6567d2",
    },
  ]);
  const [orders, setOrders] = useState([]);

  const addToOrder = useCallback((id) => {
    setOrders((orders) => {
      const finded = orders.find((order) => order.id === id);

      if (finded === undefined) {
        return [...orders, { id, quantity: 1 }];
      } else {
        return orders.map((order) => {
          if (order.id === id) {
            return {
              id,
              quantity: order.quantity + 1,
            };
          } else {
            return order;
          }
        });
      }
    });
  }, []);
  const remove = useCallback((id) => {
    setOrders((orders) => {
      return orders.filter((order) => order.id !== id);
    });
  }, []);
  const removeAll = useCallback(() => {
    setOrders([]);
  }, []);

  return (
    <AppStateContext.Provider
      value={{
        prototypes,
        orders,
        addToOrder,
        remove,
        removeAll,
      }}
    >
      {children}
    </AppStateContext.Provider>
  );
};

export default AppStateProvider;

```

#### orders


```

import { useMemo } from "react";
import useActions from "../hooks/useAction";
import useOrders from "../hooks/useOrders";
import usePrototypes from "../hooks/UsePrototypes";
export default function Orders() {
  const orders = useOrders();
  const prototypes = usePrototypes();
  const { remove, removeAll } = useActions();

  const totalPrice = useMemo(() => {
    return orders
      .map((order) => {
        const { id, quantity } = order;
        const prototype = prototypes.find((p) => p.id === id);
        return prototype.price * quantity;
      })
      .reduce((l, r) => l + r, 0);
  }, [orders, prototypes]);

  if (orders.length === 0) {
    return (
      <aside>
        <div className="empty">
          <div className="title">You don't have any orders</div>
          <div className="subtitle">Click on a + to add an order</div>
        </div>
      </aside>
    );
  }

  return (
    <aside>
      <div className="order">
        <div className="body">
          {orders.map((order) => {
            const { id } = order;
            const prototype = prototypes.find((p) => p.id === id);
            const click = () => {
              remove(id);
            };
            return (
              <div className="item" key={id}>
                <div className="img">
                  <video src={prototype.thumbnail}></video>
                </div>
                <div className="content">
                  <p className="title">
                    {prototype.title} x {order.quantity}
                  </p>
                </div>
                <div className="action">
                  <p className="price">$ {prototype.price * order.quantity}</p>
                  <button
                    className="btn btn--link"
                    onClick={() => {
                      click();
                    }}
                  >
                    <i className="icon icon--cross" />
                  </button>
                </div>
              </div>
            );
          })}
        </div>
        <div className="total">
          <hr />
          <div className="item">
            <div className="content">Total</div>
            <div className="action">
              <div className="price">${totalPrice}</div>
            </div>
            <button
              className="btn btn--link"
              onClick={() => {
                removeAll();
              }}
            >
              <i className="icon icon--delete"></i>
            </button>
          </div>
        </div>
        <button
          className="btn btn--secondary"
          style={{ width: "100%", marginTop: 10 }}
        >
          Checkout
        </button>
      </div>
    </aside>
  );
}


```


#### userorder & useActions 

```

import { useContext } from "react";
import AppStateContext from "../contexts/AppStateContext";

export default function useOrders() {
  const { orders } = useContext(AppStateContext);
  return orders;
}


import { useContext } from "react";
import AppStateContext from "../contexts/AppStateContext";

export default function useActions() {
  const { addToOrder, remove, removeAll } = useContext(AppStateContext);
  return { addToOrder, remove, removeAll };
}


```
