# Spy
# Stub
# Mock

# capacitaciones-crombie

```
import ErrorResponse from "Helpers/ErrorResponse";
// const updateUCC = jest.fn((event) => 'Invoke updateUCC for handling POST method');
// const getUCCInfo = jest.fn((event) => 'Invoke getUCCInfo for handling GET method');
import { updateUCC } from '../updateUCC';
import getUCCInfo from '../getUCCInfo';
import { handler } from '../index';
jest.mock('../updateUCC', () => ({ updateUCC : jest.fn() }));
jest.mock('../getUCCInfo', () => ({ getUCCInfo : jest.fn() }));

// Crear una función manejadora separada para que Jest pueda espiar
// const handler = (event : any) => {
//   if (event.requestContext.http.method === "POST") {
//     return updateUCC(event);
//   } else if (event.requestContext.http.method === "GET") {
//     return getUCCInfo(event);
//   }
//   throw ErrorResponse("Invalid method");
// };

describe('orderUCC', () => {
  beforeEach(() => {
    process.env.WOLTERS_KLUWER_TOKEN = 'token';
    process.env.WOLTERS_KLUWER_URL = 'url';
  });
  afterEach(() => {
    jest.clearAllMocks(); // Limpiar los mocks después de cada test
  });

  it('Validate POST Method', () => {
    const event = {
      requestContext: {
        http: {
          method: "POST"
        }
      }
    };

    handler(event); // Llamamos al handler con evento POST

    // Verificamos que updateUCC fue llamado
    expect(updateUCC).toHaveBeenCalled();
    expect(updateUCC).toHaveBeenCalledWith(event); // Verificamos que fue llamado con el evento correcto
  });

  // it('Validate GET Method', () => {
  //   const event = {
  //     requestContext: {
  //       http: {
  //         method: "GET"
  //       }
  //     }
  //   };

  //   const result = handler(event); // Llamamos al handler con evento GET

  //   // Verificamos que getUCCInfo fue llamado y devolvió el valor esperado
  //   expect(getUCCInfo).toHaveBeenCalled();
  //   expect(result).toEqual('Invoke getUCCInfo for handling GET method');
  // });

  // it('Invalid method throws error', () => {
  //   const event = {
  //     requestContext: {
  //       http: {
  //         method: "DELETE"
  //       }
  //     }
  //   };

  //   // Verificamos que se lanza el error para métodos no válidos
  //   expect(() => handler(event)).toThrow("Invalid method");
  // });
});
```
